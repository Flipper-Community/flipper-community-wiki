# Pull Request Guide
This guide seeks to provide some information for those who may not have much experience with GitHub, git, or pull requests but wish to add to the wiki.
Instructions are intended to be followed on a personal computer. 

## Prerequisites
To make a pull request, you'll need the following items:

- An installed copy of [Git](https://git-scm.com/downloads)
- A GitHub account that you have created and signed in to

## Pull Request Process
Below is the general workflow that a pull request requires:

1. [Fork the GitHub repository](#forking-the-github-repository)
1. [Clone to your local computer](#cloning-to-your-pc)
1. [Make your changes](#make-your-changes)
1. [Use git to commit changes back up to GitHub](#commit-changes-back-to-github)
1. [Create a pull request on GitHub](#create-a-pull-request)


### Forking the GitHub Repository

After one has signed into their GitHub account, you should now see a `Fork` button at the top right area on the [Flipper Community Wiki](https://github.com/Flipper-Community/flipper-community-wiki). 
To fork the Flipper Community Wiki: do the following:

1. Click the `Fork` button
1. be sure the Owner is set to your own account
1. Either leave the Repository Name as default, or change it to your liking. 
1. Be sure "Copy the `master` branch only" is selected
1. Click "Create Fork"

You should now have your own copy of the wiki in your own repository to change as you like. 

### Cloning to your PC
1. Browse to your profile on GitHub
1. Click **Repositories**
1. Find the wiki fork you created in the [forking step](#forking-the-github-repository) and click to navigate to it
1. Click the green `Code` button, then choose **HTTPS**
1. Copy the URL that GitHub provided
1. On your PC, decide on a easily accessible folder that you'd like to copy files into (I.E. a folder created on your desktop or something)
1. Open up a terminal on your PC (typically this will be Powershell or Bash depending on OS)
1. `cd` into the easily accessible folder you created in the earlier step. 
1. Type `git clone ` then paste the URL you copied earlier and press enter. The files should copy down
    - the command should look like `git clone https://github.com/YourUserNameHere/flipper-community-wiki.git` assuming you kept the default name during the fork process.

### Make your changes
You are now ready to add to the wiki. 
Refer to the [main readme for getting mkdocs set up and testing your changes](README.md).
Then return to this guide once you have your changes in place. 

### Commit changes back to GitHub
Once you are done making changes to the wiki, we will then need to add our changes to git and create a commit to store them. 
We will also only want to add files we have added or changed, and nothing else. 

1. Open up a terminal and `cd` into the flipper wiki folder that was created during the [clone to your pc](#cloning-to-your-pc) step. 
1. Run `git status` to see what files you have changed/modified. you should see the new files you added as untracked files and files you changed as modified files. 
1. For each `.md` or `.yml` file you have modified, run `git add path/to/your/file` replacing the `path/to/your/file` section with the location of the file(s) you have added/changed.
1. If you created a page that added images, use the `git add` command to add the entire folder of images you added to any wiki sections.
1. Verify all the files you added and need are listed as "changes to be committed" by running `git status` again.
1. If everything looks correct, we are now ready to commit this. 
1. Run `git commit -m "Your message here providing a short description of changes made"` to create a commit.
    - if this is your first time running git, it will prompt you about setting your name and email. You will need to set these to whatever you like (doesn't have to be real info if you do not desire it to be so). Just run the commands it provides to set your email and name, the re-run the commit command above. 
1. We can now push this up to GitHub by running `git push origin master`
    - This should prompt git to ask you for your GitHub login username and password if it is your first time. Go ahead and enter this in.
1. If all goes well, the command should complete without raising any errors.
1. Verify your files are now on GitHub under your wiki repository on the website.

### Create a Pull Request
After making any needed commits to GitHub, you are now ready to create a Pull Request on the Flipper Community Wiki. 

1. Navigate to your copy of the community wiki on GitHub
1. In the top left area, click the **Pull requests** tab
1. On the right upper side, click **New pull request**
1. At the top of this page, you will have an area that describes how the data to flow
    - On the left, the base repository should be the main `Flipper-Community/flipper-community-wiki` set to `master`
    - On the right should be your repository for your copy of the wiki, also set to `master`
1. In the lower area of the screen, it will detail all changes made. read through these and verify the changes are what you expect
1. If all items look correct, click **Create pull request** at the upper right corner.
1. You will now be prompted to fill in a title for this change request, as well as a description
    - make the title a very short summary of what you are wanting to add/change
    - Fill in the description area with any other information that may be beneficial for the reviewer to know. 
1. Once info has been filled in, simply click **Create pull request** 

You have now completed your first pull request! Your submission will then be evaluated and if everything looks correct, added to the wiki!

Once your changes have been merged and the pull request has been closed, you may then optionally delete your copy of the wiki on your account, as it is no longer needed after the changes are merged. 
