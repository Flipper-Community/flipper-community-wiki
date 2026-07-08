# Flipper Zero Python Protobuf guide
The Flipper Zero supports receiving commands via protobuf encoded communications via both USB and GPIO. Protobuf communication allows you to do a number of different items via external controls such as:

- press buttons
- read/write files
- draw on the screen
- set GPIO pin states

and many other functions. While very flexible in their abilities to send/receive varying forms of data, they are also a bit more complex to handle due to the encoding step one needs to complete beforehand so that you can use these commands in your Flipper Zero applications. In order to do this, the official method is to use what is referred to as a **protobuf compiler** to do this and generate what you need. 

There are multiple protobuf compilers that will generate these encodings (The official protobuf toolset, nanopb, etc). They can also be encoded by hand if one studies the structure of the data encoding. This guide will assume low/no knowledge of protobufs and data structures and will try to aim for the path of least resistance. 

## Python: Press a key via protobuf
For this tutorial, we will set up a basic python environment to handle protobuf and simply send a short press of the UP key on the Flipper Zero to demonstrate how to use protobufs. 

### Prereqs
For this python tutorial we will stick with the [official protobuf implementation](https://github.com/protocolbuffers/protobuf) to compile and generate the encodings we need. 
Simplified OS specific instructions are as follows for getting this installed:

- Windows: run `winget install Google.Protobuf`
- Mac: `brew install protobuf`
- Linux: the `protobuf` package should be in most distros package managers

### Environment setup
First, we will need to grab the protobuf descriptor files from [the flipperzero-protobuf repo](https://github.com/flipperdevices/flipperzero-protobuf). 
if git is installed, you can just grab those via `git clone https://github.com/flipperdevices/flipperzero-protobuf.git` into where our project folder will be. 
Otherwise, you can just download the zip under the green **Code** button on github, then extract it. You should now have a `flipperzero-protobuf` folder. 
From here, we need to then compile these files to generate the needed python bindings.

Open a terminal, then make sure you've moved into the project folder that has your `flipperzero-protobuf` folder and follow these steps:

1. `cd` into the `flipperzero-protobuf` folder
2. create a `pythonproto` folder
3. run `protoc --python_out=pythonproto *.proto` to compile and generate the python files off of the protobuf files

If done correctly, you should now have multiple python files in the `pythonproto` folder. Each of these files are associated with the underlying .proto file in the parent directory. 

1. `cd` back up to your project directory. 
1. set up our python virtualenv to hold any packages we need to install via `python -m venv venv`
1. After this completes, run the following depending on OS:
    - Windows: `venv/bin/activate`
    - Linux/mac: `source venv/bin/activate`

If you see the `(venv)` bit at the front of your terminal line, you should have it activated. 

#### Getting needed libraries
Next, we need to install **protobuf** and **pyserial** for python to handle our generated files: 

`pip install protobuf pyserial`

Now do these two steps: 

1. Move the pythonproto folder back to your main project directory that holds the `venv` folder from earlier. 
    - If done correctly you should have a `venv` folder and a `pythonproto` folder side by side. 
Our generated files rely on the `protobuf` library being installed and call for it, even though we will be just calling the python protobuf files. 

1. Create a blank `main.py` file. 

### Python coding
Now we are ready to begin making our basic python script to set up and call our new shiny RPC commands we generated with protobuf. 


At the top of your `main.py` file, put the following lines:
```python
import serial, sys, time
import serial.tools.list_ports # pyserial has some stuff to help us detect things like the flipper automatically
sys.path.append('pythonproto/') # add the compiled proto python files to the path so it can easily see them and you dont have import errors
import flipper_pb2
import gui_pb2
```
This imports the .py files from the pythonproto folder we created and moved earlier. 


For the next section, we can leverage pyserial's power of finding serial ports by their description:
```python
# use pyserial's port listing power to scan through all serial ports and look for "flipper"
def find_flipper():
    ports = serial.tools.list_ports.comports()
    for port in ports:
        if "Flipper" in port.description:
            print(f"Found it! Port: {port.device}")
            return port.device
    # if we dont find anything, raise an error.
    raise ConnectionError("Can't find flipper on a serial port.\nIs it plugged in?")
```

We follow this up with two small lines to set a variable to hold our serial port attributes, then turn on serial Request-To-Send mode:
```python
ser = serial.Serial (flipper_port, 115200, timeout=1, dsrdtr=True) # set up our serial connection options.
ser.rts = True # turn on rts
```

Next we add a function to create our protobuf message layout. Protobuf expects the message to be structured a certain way:

- contain a unique command ID attribute, so that it can tell each command we send is unique and not repeated
- for button presses, it also needs a input key, and and input type.
    - These items are laid out more in depth in the .proto files we downloaded earlier. 

```python
def create_button_message(command_id, input_key, input_type):
    """Creates the proper format of how our button press message should look"""
    main_msg = flipper_pb2.Main() # the main class for flipper_pb2 has a lot of error checking stuff if one wants to use it (we arent here) and also a settable attribute for command_id, which we will need.
    main_msg.command_id = command_id # Assign a unique ID, protobuf expects each command to be labeled with a unique ID, preferable sequention, so it knows that a given command is not just being repeated.
    main_msg.gui_send_input_event_request.key = input_key # the key we want to press
    main_msg.gui_send_input_event_request.type = input_type # input type we want (long,short, etc)
    return main_msg
```
Protobuf is a lower level protocol.
It needs to know how long a message is going to be before it reads the rest of the message.
We have to tell it manually on each message "hey, this is the size to expect" before we send it what we actually want to do.
In order to handle this, it uses a thing called a "variable length integer".
This uses bit-shifting math magic that is a bit complex for the average person, and requires some familiarity with bitwise operations. 
If you want to read about the logic behind it, check out [this blog post](https://victoriametrics.com/blog/go-protobuf/).

Let's set up a function to handle setting this variable length integer and the math behind it, so that we don't have to think about it or do math ourselves: 

```python
def send_message(serialvar, main_message): # set up our message sender function, allowing it to have two variables for input
    data = main_message.SerializeToString() # feed our main_message to the protobuf string serializer
    length = len(data) # protobuf needs to know how long a message is, so we will get this count here so we can do dark magic math on it later.
    # evil bit math below for setting how long the message will be for protobuf
    while length >= 0x80:
        ser.write(bytes([(length & 0x7F) | 0x80]))
        length >>= 7
    serialvar.write(bytes([length])) # write to tell protobuf how long our message will be
    serialvar.write(data) # send the data
```

Now we need some regular serial commands to get the Flipper Zero set to protobuf RPC mode:

```python
ser.reset_input_buffer() # make sure our serial input is empty
time.sleep(0.1)
ser.write(b"\r") # press the enter key on the serial CLI to wake a possible sleeping flipper up
time.sleep(0.1)
ser.read(4096) # grab any data the flipper cli outputs, and acknowledge we read it.
ser.write(b"start_rpc_session\r") # send the start_rpc_session command over flipper CLI
time.sleep(0.5)
ser.reset_input_buffer() # clean out anything sitting in ther serial buffer that you got from the flipper earlier.
```

After ALL of this, we can finally add the last two lines to send off our button presses to the Flipper Zero:

```python
send_message(ser, create_button_message(1, gui_pb2.UP, gui_pb2.PRESS)) # send the pressing of the UP key
send_message(ser, create_button_message(2, gui_pb2.UP, gui_pb2.SHORT)) # tell it to press and release that key for a SHORT
```







### The completed python file

Putting it all together to handle sending a button press:
```python
import serial, sys, time
import serial.tools.list_ports # pyserial has some stuff to help us detect things like the flipper automatically
sys.path.append('pythonproto/') # add the compiled proto python files to the path so it can easily see them and you dont have import errors
import flipper_pb2
import gui_pb2

# use pyserial's port listing power to scan through all serial ports and look for "flipper"
def find_flipper():
    ports = serial.tools.list_ports.comports()
    for port in ports:
        if "Flipper" in port.description:
            print(f"Found it! Port: {port.device}")
            return port.device
    # if we dont find anything, raise an error.
    raise ConnectionError("Can't find flipper on a serial port.\nIs it plugged in?")

flipper_port = find_flipper() # set the port variable to wherever it found the flipper

ser = serial.Serial (flipper_port, 115200, timeout=1, dsrdtr=True) #set up our serial connection options.
ser.rts = True #flip on rts

# we need to set up a button message the flipper would understand.
# for this function, we have 3 variables we can feed it: the command ID, the input key we want to press, and the input type (press, release, short, long, etc.)
def create_button_message(command_id, input_key, input_type):
    """Creates the proper format of how our button press message should look"""
    main_msg = flipper_pb2.Main() #the main class for flipper_pb2 has a lot of error checking stuff if one wants to use it (we arent here) and also a settable attribute for command_id, which we will need.
    main_msg.command_id = command_id # Assign a unique ID, protobuf expects each command to be labeled with a unique ID, preferable sequention, so it knows that a given command is not just being repeated.
    main_msg.gui_send_input_event_request.key = input_key #the key we want to press
    main_msg.gui_send_input_event_request.type = input_type #input type we want (long,short, etc)
    return main_msg


# protobuf is a lower level protocol
# it needs to know how long a message is going to be, before it reads the rest of the message.
# so we have to tell it manually on each message "hey, this is the size to expect"
# in order to handle this, it uses a thing called a "variable length integer".
# This uses bit-shifting math magic
# if you want to read about it, check out https://victoriametrics.com/blog/go-protobuf/
def send_message(serialvar, main_message): # set up our message sender
    data = main_message.SerializeToString() # feed out message to the protobuf string serializer
    length = len(data) # protobuf needs to know how long a message is, so we will get this count here so we can do dark magic math on it later.
    # evil bit math below for setting how long the message will be for protobuf
    while length >= 0x80:
        ser.write(bytes([(length & 0x7F) | 0x80]))
        length >>= 7
    serialvar.write(bytes([length])) # write to tell protobuf how long our message will be
    serialvar.write(data) # send the data


# here we run needed Serial commands to get the flipp out of normal CLI mode and into protobuf mode.
ser.reset_input_buffer() # make sure our serial input is empty
time.sleep(0.1)
ser.write(b"\r") # press the enter key on the serial CLI to wake a possible sleeping flipper up
time.sleep(0.1)
ser.read(4096) # grab any data the flipper cli outputs, and acknowledge we read it.
ser.write(b"start_rpc_session\r") # send the start_rpc_session command over flipper CLI
time.sleep(0.5)
ser.reset_input_buffer() # clean out anything sitting in ther serial buffer that you got from the flipper


# much code later, we can finally send stuff to our flipper zero!
# we tell send_message to use our serial attributes stored in 'ser', and give it to the send_message to send
send_message(ser, create_button_message(1, gui_pb2.UP, gui_pb2.PRESS)) # send the pressing of the UP key
send_message(ser, create_button_message(2, gui_pb2.UP, gui_pb2.SHORT)) # tell it to press and release that key for a SHORT amount of time.
```

