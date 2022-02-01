# Branches

Lab Objectives:
- Create a branch in Bitbucket
- Make changes locally and push to Bitbucket
- Pull changes from Bitbucket

## Prerequisites

You should have completed Lab 2.2.

## Lab

### Create a branch in Bitbucket

In Bitbucket, go to the "Coffee Bar" repository.  You should be able to get to it quickly from the `Repositories` drop down in the top menu bar.

Click on the `Branches` menu item in the left menu panel to show the current branches in the repository.  Only one branch "main" should be listed.

Click on the `Create branch` menu item in the left menu panel.  This will open a "Create branch" form page. Populate the form fields:
* Repository - Make sure the "Coffee Bar" repository is selected.
* Branch type - Change the type to "Feature".  Notice that the Branch name field gets a "feature/" prefix.  We will discuss branch prefixes a bit later.
* Branch from - Select "main".
* Branch name - Enter "lab 2.3" after the "feature/" prefix.

Click the `Create branch` button.  The "Source" page will display showing code for the new branch.

### Fetch new branch to local repository

To make code changes on the new branch, you will want to have the new branch in the repository on your local machine.  Do you remember what Git command we would use?  Let's go through the steps.

On your local machine, go to the directory for the repository you created in Lab 1.1.  Then execute the Git command to see what branches already exist there.
```
git branch -a
```

Fetch the latest state from Bitbucket and then re-examine what branches exist locally.
```
git fetch
git branch -a
```

Notice that the new branch shows up as a remote branch.  But in order to work on the branch, we need it as a local branch. Checkout the branch and then confirm you are now on the new branch locally.
```
git switch feature/lab-2.3
git status
```

### Make a change locally and push to Bitbucket

Make changes to `menu.txt` and `welcome.txt` as two new commits.
```
vi menu.txt
git add .
git commit -m "Local changes to menu file"
```
```
vi welcome.txt
git add .
git commit -m "Local changes to welcome file"
```

Check the Git status.  You will see that the local branch is now ahead of the remote branch.  Push the changes to Bitbucket.
```
git status
git push
```

Go to the Bitbucket UI.  If you are not already on the "Source" page for the repository, click on the `Source` menu item in the left menu panel.  Be sure that the "feature/lab-2.3" branch is selected on the page.  Then click on the `menu.txt` filename to show the contents of the file.  Confirm that the local change shows up in Bitbucket.

#### See changes by examining commits

Click on the `Commits` menu item in the left menu panel. Confirm that the local commits show up in commit graph in Bitbucket.  Click on the commit hash link to open the commit details, and see that the diff shows that change made in the commit.

#### See changes by branch comparison

Let's now do a branch compare.  Click on the `Compare` menu item in the left menu panel. This opens a compare page.
* Select the "feature/lab-2.3" branch as the Source branch.
* Leave "main" as the Destination branch.

Look at the file diffs.  Then click on the `Commits` sub-tab to see the two commits made on the new branch.

### Pull changes from Bitbucket to local repository

Let's now consider the case when a separate developer has pushed a change to your branch in Bitbucket.  You will need to pull those changes to your local machine.

#### Simulate changes pushed to Bitbucket by another developer

To simulate a change pushed to Bitbucket by a different user, we will simply edit a file within Bitbucket itself.
> In general, editing files directly in Bitbucket is discouraged as a common practice.

In Bitbucket, click on the `Source` menu item in the left menu panel.  On the shown "Source" page, be sure the "feature/lab-2.3" branch is selected.

Click on the `menu.txt` filename in the file list to show the file content.  Then click on the `Edit` button.

Make a change to the file content.  Then click on the `Commit` button in the lower right of the page.  In the "Commit file" dialog, you can keep the commit message.  Just click the `Commit` button in the dialog.

Click on the `Commits` menu item in the left menu panel to show the commits, and confirm the commit has been created.

#### Pull changes to local machine

Go back to the terminal window on your local machine.  Make sure you are on the "feature/lab-2.3" branch and check the status. The status will show that the local branch is up to date with the remote.  Do you know why?
```
git status
```

Fetch the current state from Bitbucket.  Then check the branch status again.  Now the status should show that the local branch is behind the remote branch.
```
git fetch
git status
```

Finally to get the changes into your local branch, do a Git pull.
```
git pull
git status
```

Examine the file contents on your local machine to confirm it was updated from Bitbucket.
