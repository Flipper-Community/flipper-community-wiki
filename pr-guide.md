# Pull Request Guide
This guide seeks to provide some information for those who may not have much experience with github, git, or pull requests but wish to add to the wiki.
Instructions are intended to be followed on a personal computer. 

## Prerequisites
To make a pull request, you'll need the following items:

- An installed copy of [Git](https://git-scm.com/downloads)
- A Github account that you have created and signed in to

## Pull Request Process
Below is the general workflow that a pull request requires:

1. Fork the Github repository
1. Clone to your local computer
1. Make your changes
1. Use git to commit changes back up to Github
1. Create a pull request on Github


### Forking the Github Repository

After one has signed into their Github account, you should now see a `Fork` button at the top right area on the [Flipper Community Wiki](https://github.com/Flipper-Community/flipper-community-wiki). 
To fork the Flipper Community Wiki: do the following:

1. Click the `Fork` button
1. be sure the Owner is set to your own account
1. Either leave the Repository Name as default, or change it to your liking. 
1. Be sure "Copy the `master` branch only" is selected
1. Click "Create Fork"

You should now have your own copy of the wiki in your own repository to change as you like. 

### Cloning to your PC
1. Browse to your profile on Github
1. Click Repositories
1. Find the wiki fork you created in the [forking step](#forking-the-github-repository) and click to navigate to it
1. Click the green `Code` button, then choose **HTTPS**
1. Copy the URL that github provided
1. On your PC, decide on a easily accessible folder that you'd like to copy files into (I.E. a folder created on your desktop or something)
1. Open up a terminal on your PC (typically this will be Powershell or Bash depending on OS)
1. `cd` into the easily accessible folder you created in the earlier step. 
1. Type `git clone ` then paste the URL you copied earlier and press enter. The files should copy down
    - the command should look like `git clone https://github.com/YourUserNameHere/flipper-community-wiki.git` assuming you kept the default name during the fork process.

### Make your changes
You are now ready to add to the wiki. 
Refer to the [main readme for getting mkdocs set up and testing your changes](README.md).
Then return to this guide once you have your changes in place. 

### Commit changes back to Github
Once you are done making changes to the wiki, we will then need to add our changes to git and create a commit to store them. 
We will also only want to add files we have added or changed, and nothing else. 

1. open up a terminal and `cd` into the flipper wiki folder that was created during the [clone to your pc](#cloning-to-your-pc) step. 
1. run `git status` to see what files you have changed/modified. you should see the new files you added as untracked files and files you changed as modified files. 
1. for each `.md` or `.yml` file you have modified, run `git add path/to/your/file` replacing the `path/to/your/file` section with the location of the file(s) you have added/changed
1. if you created a page that added images, use the `git add` command to add the entire folder of images you added to any wiki sections.
1. verify all the files you added and need are listed as "changes to be committed" by running `git status` again
1. If everything looks correct, we are now ready to commit this. 
1. run `git commit -m "Your message here providing a short description of changes made"` to create a commit
1. we can now push this up to Github by running `git push origin/master`



