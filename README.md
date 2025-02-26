# Flipper Community wiki
This is the repo for the [Flipper community wiki](https://flipper.wiki).
If you'd like to contribute to this wiki, you may [fork the repo and offer your changes as a pull request](pull-request-guide.md).
Please be sure submissions meet the [contribution guidelines](https://flipper.wiki/contributing/).

# Technical Info
This wiki is built using the python based mkdocs builder utilizing the material theme (mkdocs-material).

It is recommended, but not required, that contributors looking to add content run the wiki locally to verify formatting behaves as expected before submitting a pull request to verify the content looks as expected and ensure a smooth pull request process.
To do so, you will need either a copy of [Git](https://git-scm.com/downloads) or the [Github client](https://github.com/apps/desktop) installed to your PC. 

You will then need to fork this repo using the fork button on this Github page to your own Github account, clone it to to your PC, make changes, then submit a Pull Request. 

#### If you are unfamiliar with using git and making pull requests on Github, see the [Pull Request Guide](pull-request-guide.md)

# Setup Guide: Running this Wiki Locally

First, clone your forked copy to your local computer so that you can make changes to it.
Once you have completed that, you can move to setting up MkDocs-Material locally using one of the options below for your platform. 

The [Python virtual environment method](#Method-2-Install-using-a-Python-virtual-environment) is HIGHLY recommended, however not everyone will feel comfortable with using python directly to install things. For that, alternate instructions are provided for convenience. 


## Operating system install directions
These options are for those who are less comfortable with messing around with python and would prefer to just install something on their system. 

### Windows 11
For this, we will use the awesome tiny [uv](https://astral.sh) utility to manage pulling in stuff from python without needing to install python or risking your existing python setup.

1. Open up Powershell
1. run `winget install astral-sh.uv`
1. Hit yes on any prompts, and wait for the install to finish. 
1. close and re-open Powershell. 
1. Using git or the Github client, clone your fork of the docs to your PC. 
1. In Powershell, `cd` into the `flipper-community-wiki\flip-wiki` folder that you got from cloning your fork onto your PC. 
1. simply run `uvx --from mkdocs-material mkdocs serve` to launch mkdocs seamlessly without installing anything to your PC.
    - Note: the tool will say `warning: An executable named mkdocs is not provided(...)`, you can safely disregard this, as mkdocs-material just looks odd the way its set up to this utility.  
1. when done running mkdocs, simply press **Ctrl+c** to stop.

Like a browser, `uv` keeps a cache around for items you've used before to reduce download times. If you want to wipe it, you can simply do `uv cache clean` to delete everything. 

After this, you can optionally uninstall `uv` when done if you have no further need of it by simply doing `winget uninstall astral-sh.uv`, which will return your system to the state it was in prior to installing it. 

----

### Linux
MkDocs is available directly through the package manager for most common distros. 

- Ubuntu 24.04 and newer: `# apt install mkdocs-material`
- Debian 12 and newer: `# apt install mkdocs-material`
- Fedora 41 and newer: `# dnf install mkdocs-material`
- Arch: `# pacman -S mkdocs-material`

Once installed, `cd` into the `flipper-community-wiki/flip-wiki` folder and run `mkdocs serve`

----

### Mac
MkDocs can be installed via [Brew](https://brew.sh):
`brew install mkdocs-material`

Once installed, `cd` into the `flipper-community-wiki/flip-wiki` folder and run `mkdocs serve`

----

## Python setup (platform agnostic)
MkDocs-Material is built entirely on the Python platform, and can be installed on just about any device capable of running Python. 

**There are two methods** you can opt to install this, depending on preference:

### Method 1: Install Directly using Python
This method wil directly install MkDocs into whatever python version you are running. It is not the cleanest way to do this, but it is the simplest. 

1. run `pip install mkdocs-material`
1. wait for the setup to complete. 
1. `cd` to the directory you cloned the `flipper-community-wiki` folder and enter it. 
1. `cd` into the `flip-wiki` folder
1. run `python -m mkdocs serve`
1. MkDocs will begin running at `http://127.0.0.1:8000`, browse to this in your browser
1. Verify the wiki appears and the changes you made to the wiki appear as expected. 

----

### Method 2: Install using a Python virtual environment
This method uses a built in feature of Python called a *virtual environment*, which allows you to contain what you install to python inside of a single folder on your PC, so that is does not interfere with anything else on your computer, allowing you to cleanly delete the folder when done and remove all trace of what you installed (in this case, MkDocs). 

1. Using git or the Github Desktop app, clone your fork of the wiki to your desktop. 
1. You should now have a `flipper-community-wiki` folder. 
1. open up Powershell or your preferred terminal and `cd` inside of this folder. 
1. run `python -m venv venv` and wait for this to complete. 
1. once done, you will have a new folder called `venv` sitting in the folder
1. Activate the virtual environment by doing the following:
    - Windows: run `venv\scripts\activate.ps1`
    - Linux/Mac: run `source venv/bin/activate`
1. you should now see `(venv)` added in your terminal. This means that so long as this is active, anything installed will be contained entirely in the `venv` folder we created. 
1. run `python -m pip install mkdocs-material` and wait for the install to finish. 
1. `cd` into the `flipper-community-wiki/flip-wiki` folder
1. once complete, run `python -m mkdocs serve` to start
1. MkDocs will begin running at `http://127.0.0.1:8000`, browse to this in your browser
1. Verify the wiki appears and the changes you made to the wiki appear as expected. 

When done, you can close out the virtual environment by typing `deactivate` in your terminal. If you need to re-activate it again later, just run the "Activate the virtual environment" steps above again. 



## Adding New Pages
1. [Fork this Github repo and clone your copy to your PC](pull-request-guide.md). 
1. Optionally install mkdocs using the above instructions if you don't have it to preview pages (strongly recommended)
1. Enter the `flip-wiki/docs` folder
1. Create whatever doc files you want in named `.md` files.
1. Once done, add them to the `flip-wiki/mkdocs.yml` towards the bottom under the `Navigation Heirarchy` section, following the pattern of the other `.md` files.
1. If the preview looks good when using mkdocs to preview them, submit a pull request. 

For more in depth features, see the [MkDocs-material guide](https://squidfunk.github.io/mkdocs-material/reference/)
