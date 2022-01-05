# Git Commands for Interacting with Bitbucket

Lab Objective:
- Clone a Bitbucket repository
- Push changes to Bitbucket
- Fetch and pull changes from Bitbucket

## Prerequisites

You should have uploaded your SSH key to Bitbucket.  Otherwise you can use HTTPS for the git operations, but will need to enter your username and password.

## Lab

### Create a new Bitbucket repository from local repository

Go to the Bitbucket UI and find the "Training Labs" project you created earlier.  In the left navigation, click `Create repository`.  Enter the name "Git Labs Repo" and click `Create`.

The resulting page will show that you have an empty repository, along with instructions on how to populate content into the repository.

Copy the line in the instructions to set a remote.

In a terminal shell window, go to your local repository, then paste in the git command.
```
git remote add origin <repo-URL>
```

Confirm the remote has been added.
```
git remote -v
```

Now push your local repository to Bitbucket.
```
git push origin --all
```

Now refresh the page in Bitbucket to confirm you local repository is now in Bitbucket.

### Make some local changes and push to Bitbucket

Create a new branch called `feature-two`.
```
git switch -c feature-two
```

Open the `afile.txt` for edit and make some changes. Commit the changes.
```
vi afile.txt
git add -A
git commit -m "changed afile in feature-two"
```

Push the changes to Bitbucket. (Note if you leave out the "-u origin" part of the command, Git will complain that there is no remote-tracking branch. You would not get that message if the branch did already exist on the remote.)
```
git push -u origin
```

Go to the Bitbucket UI and confirm the new branch and changes show up there.

### Pull new changes from Bitbucket

#### Simulate changes pushed to Bitbucket by another developer

In the Bitbucket UI, go to the `Sources` page for the repository, change to the `feature-two` branch.

Open the "afile.txt" file for edit in the UI. Makes some content changes, and commit the change.

#### Fetch the remote state

In your terminal window, execute a Git fetch to get the latest status of the remote repository. Then do a status to see that the `feature-two` branch is behind the remote.  You can also see this in the graphical commit history.
```
git fetch
git status
git log --oneline --graph --all
```

#### Merge the changes from the remote to your local repository

Do a git pull to merge the remote feature-two branch to your local feature-two branch.  Then do a status to confirm you branch is up to date.
```
git pull
git status
```

=======================================

### Clone a Bitbucket repository

Go to the Bitbucket UI and find the "imported-repository" repository you created in Lab 3.1

On the repository page and click the `clone` button.  Select the appropriate protocol (HTTP or SSH) in the upper right of the pop-up dialog.  Copy the shown clone command.

In a terminal shell window, go to the temporary directory that is the parent for the lab repositories.

Enter the copied clone command into the terminal shell.  The clone command will download the repository into a new subdirectory.
```
git clone <your-repository-URL>
```

Go to the created subdirectory and confirm the repository was copied.

### Make some local changes and push to Bitbucket

Check out the `feature` branch.  Notice that Git automatically creates a new local branch that tracks the remote feature branch.
```
git checkout feature
```

In your new repository on your local machine, go to the `/src` folder.  Open the `test.js` file for edit and make some changes. Commit the changes.
```
vi test.js
git add -A
git commit -m "changed test.js"
```

Push the changes to Bitbucket.
```
git push
```

Go to the Bitbucket UI and confirm the changes show up there.
