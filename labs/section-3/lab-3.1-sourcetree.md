# Using Sourcetree

Lab Objectives:
- Connect to Bitbucket from Sourcetree
- Push changes to Bitbucket from Sourcetree
- Pull changes to Sourcetree from Bitbucket

## Prerequisites

You should have Sourcetree installed on your local machine.  If not, please do it now by following instructions at: https://www.sourcetreeapp.com/

## Lab

In this lab, we will be using Sourcetree to interact with Bitbucket.  Consequently the lab will involve often switching back and forth between Sourcetree and Bitbucket as we make changes in one application and want to see the result in the other application.

### Configure Sourcetree

#### Check Sourcetree settings

On your local machine, open the Sourcetree application.

Open the setting dialog:
- On Windows, this will be the `Options` sub-menu item under the `Tool` menu on the top menu bar.
- On Mac, this will be the `Preferences` sub-menu item under the `Sourcetree` menu on the top menu bar.

On the "General" tab in the dialog, confirm your name and email address are populated for "Default user information".  Sourcetree may have pre-populated the values from your local Git installation. If the fields are empty, then populate them as you would have done for the Git configuration.

Further down, there should be a "Project folder" field.  Set the value to the parent folder of the repository you created in an earlier labs.  We will be using Sourcetree to create a new repository in that parent folder.

Click on the "Git" tab.  Scroll down to check the Git version.  For this lab, you can use either the Embedded or System version of Git.

#### Connect to Bitbucket

Let's add the lab Bitbucket instance as a new account in Sourcetree.

**For Windows:**
1. Click on the "Authentication" tab in the settings dialog window.
2. Click the `Add` link.
3. Select "Bitbucket Server" as Hosting Service.
4. For Host URL, copy the initial part of the Bitbucket URL (up to and including ".../bitbucket/") from the browser address and paste it into the field.
5. For Preferred Protocol, select "SSH" if you are using an SSH key for Git commands to interact with Bitbucket; otherwise select "HTTPS".
6. Select "Basic" for Authentication.
7. Enter your username and password for authenticating to Bitbucket.
8. Click `OK` to save.  You should see the new account added.

**For Mac:**
1. Click on the "Accounts" tab in the settings dialog window.
2. Click the `Add...` button.
3. Select "Bitbucket Server" as Host.
4. For the Host URL, copy the initial part of the Bitbucket URL (up to and including ".../bitbucket/") from the browser and paste in the field.
5. Enter your username and password for authenticating to Bitbucket.
6. For Protocol, select "SSH" if you are using an SSH key for Git commands to interact with Bitbucket; otherwise select "HTTPS".  (If you select "SSH", you may need to upload your **public** SSH Key.)
7. Click `Save` button.  You should see the new account added.

Close the settings dialog.  (On Windows, click the `OK` button in the lower right of the dialog.)

### Add a repository

Let's add the repository from the earlier labs.  It already exists locally and already exists in Bitbucket -- we just need to add it to Sourcetree.

For Windows:
1. Click on the `Add` top menu icon in the current tab in the Sourcetree window. A "Add a repository" page will show.
2. Click the `Browse` button to the right of the first field.  Find and select the folder that is the repository from the earlier labs.  Click the `Select Folder` button.
3. The "Working Copy Path" and "Name" fields on the "Add a repository" page will become auto-filled.  Click the `Add` button.
4. The repository should show up in the list of `Local` repositories.  If the repository view does not open automatically, double-click the repository name on the `Local` page to open the repository view.


For Mac:
1. Click on the "Window" top menu, and then select the "Show Remote Browser" sub-menu item.
2. In the dialog that pops up, click on the "New..." menu item, and the select the "Add Existing Local Repository" sub-menu item.  A Finder dialog pops up.
3. In the Finder dialog, navigate to and select the "Coffee Bar" folder that is the repository from the earlier labs.  Click the `Open` button.
4. The repository should show up in the list of `Local` repositories.  Double-click on the newly added repository to open it in the main Sourcetree window.

### Push changes to Bitbucket

#### Create a new branch

In the left menu panel, make sure "main" is the currently checked-out branch.  If it is not, then hover over the "main" branch name in the left panel, then right click and select `Checkout main` in the pop-up menu.

Click the `Repository` menu item along the top menu bar.  Select the `Branch...` sub-menu item.  A "new Branch" dialog will pop up.  (You could also have clicked on the `Branch` icon in the top toolbar.)

Name the new branch "feature-lab-3".  Click the `Create Branch` button.  The branch will get created and will be the current checked-out branch for the repository.

#### Make some code changes

Use your code editor to make changes to the `menu.txt` and `welcome.txt` files in the repository.  **Do not** use the command line to stage or commit the changes.

#### Stage and commit changes from within Sourcetree

In Sourcetree, click on the `File status` menu item in the left menu panel.  

Notice the shown file changes.  Also notice that the changed files are shown in the "Unstaged files" section.  Stage the files:
* On Windows, click the `+` to the right of the file names.  The files will move up to the "Staged files" section.
* On Mac, click on the checkbox in front of file names. The files will move up to the "Staged files" section.

At the bottom of the page, click within the "Commit message" text area.  Type in a commit message, then click the `Commit` button.

Click on the `History` menu item in the left menu panel.  Confirm that your new commit shows up at the top of the commit graph.

#### Push the new branch and commit to Bitbucket

Click the `Push` menu icon in the top tool bar. A "Push" dialog pops up.

Notice that in the list of possible branches to push, the new "feature-lab-3" branch does not have a corresponding remote branch.  Click the "Push?" checkbox in front of the branch name. Notice that the "Track?" icon changes to a check mark.

We are only pushing the new branch.  If the "Push?" checkbox is checked for any other branches (e.g., main), uncheck those.  Click the `OK` (or `Push`) button in the dialog.

Back on the History page, notice that "feature-lab-3" now shows up as a remote branch in the commit graph and in the left menu panel.

Go to Bitbucket in your browser window.  Click on `Commits` in the left menu panel.  Select "feature-lab-3" in the Branch selection drop-down.  Confirm you see your branch and pushed commit on the Bitbucket commit graph page.

### Pull changes from Bitbucket

#### Create a new branch in Bitbucket

In Bitbucket, create a new branch off of "main".  Call the new branch "integration".

#### Checkout the new branch in Sourcetree

Go to Sourcetree.

Click `Repository` in the top menu bar and then select the `Refresh Remote Status` sub-menu item.  The new "integration" branch should show up under the Remotes section in the left menu panel.  (It may take a minute or so for Sourcetree to show the new remote branch.)

Hover over the "integration" remote branch name in the left menu panel, then right click to bring up a pop-up menu.  Click `Checkout` in the pop-up menu.  This will bring up a "Checkout" dialog.  Confirm that a new local branch will track the remote branch, and click the `Checkout` (or `OK`) button.

#### Simulate changes pushed to Bitbucket by another developer

Go back to Bitbucket.

On the "Source" page, confirm that the new branch is selected in the branch selection drop-down.

From the "Source" page, edit the `menu.txt` file.  (Remember that you can do this by clicking on the filename and then the `Edit` button.)  Make a change to the file that is similar but not quite identical as the change you made locally to the same file earlier.  (The purpose is to cause a merge conflict later.)  If you forget what edit you made to file earlier, you can see the diff for the last commit in Sourcetree.

Commit the change in Bitbucket.

#### Pull the change to Sourcetree

Go back to Sourcetree.

Click the `Fetch` menu icon in the top menu bar.  Notice that Sourcetree now shows the "integration" branch as being one commit behind the remote branch.

Click the `Pull` menu icon in the top tool bar. A "Pull" dialog pops up.

Verify that you are pulling the remote "integration" branch to the local "integration" branch.  Click the `OK` (or `Pull`) button on the dialog.

After the pull succeeds, the new pulled commit should show up in the commit History.

### Merge two branches in Sourcetree

Now let's use Sourcetree to do a merge from the feature branch to the integration branch.

Recall that for Git, the target branch of a merge must be the branch that is currently checked out.  Verify that Sourcetree shows the "integration" branch as the current checked out branch.

Hover over the "feature-lab-3" branch in the left menu panel, then right click to bring up a pop-up menu.  In the pop-up menu, select the option "Merge feature-lab-3 into integration".  A confirmation dialog will display.

In the merge confirmation dialog, click the `OK` button.  A "Merge Conflicts" warning pop-up will appear.  Click `OK` (or `Close`) in the warning dialog.

#### Resolve merge conflict

Click `File status` in the left menu panel.  Notice that `afile.txt` shows as both staged and unstaged.  The merged file is staged, but it contains Git markings demarcating the area of merge conflict.  We do not want the file committed in that state, so we will resolve the conflict in the unstaged version of the file.

Recall that Git's merge conflict markings show the change from the target branch ("integration") above the "=======" separator and the change from the source branch ("feature-lab-3") below.  In this case, we will go with the source branch's version of the change.

To resolve the conflict, click `Actions` in the top menu bar, then hover over the `Resolve Conflicts` sub-menu item, and select the `Resolve using 'Theirs'` sub-sub-menu item to use the source branch's change. A confirmation dialog will appear.  Click `OK`.

To complete the merge, you will need to commit the merge resolution.  On the `File status` view, you should now just see the file as staged.  Click into the commit text area at the bottom of the page.  A default merge commit message will appear; you can accept that message or change it, then click `Commit`.

Click on `History` in the left menu panel, and confirm you see the merge in the commit graph.

#### Push merged changes to Bitbucket

Sourcetree now shows that the local "integration" branch is ahead of the remote branch.

Click the `Push` menu icon in the top tool bar.  In the "Push" dialog, notice that this time the local integration branch is already shown as tracking the remote branch.  The "integration" branch should already be selected in the dialog.  If not, select it.  Click the `OK` (or `Push`) button.

If you want, you can go to Bitbucket to verify that the merge was successfully pushed to Bitbucket.

### Create a pull request from Sourcetree

Merges to the "main" branch should, as a good practice, always be done using a pull request.  (Though actually even merges to an integration or development branch should use a pull request as well.)

To create a pull request from Sourcetree, click `Repository` in the top menu bar, and then select the `Create Pull Request...` sub-menu item.  A Pull Request dialog pops up.

In the pull request dialog, verify that "integration" is selected as both the local and remote branch.  This will be the source branch for the pull request.  Pushing the latest changes from local to remote is not necessary since we already did that push above.

Click the `Create Pull Request on Web` button.

Bitbucket will automatically open in a new browser tab, showing the "Create pull request" page.  The "integration" branch will be already selected as the source branch and "main" (the default branch in the Bitbucket repository) will be pre-selected as the target.  Click the `Continue` button, then the `Create` button.
