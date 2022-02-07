# Jira Integration

Lab Objectives:
- Create branch from Jira
- Link Bitbucket commits to Jira
- View Bitbucket artifacts from Jira
- View Jira issues from Bitbucket

## Lab

### Log into Jira

Your instructor should provide you the URL and credentials to log into a Jira instance.  The Jira instance is already configured to integrate with Bitbucket.

### Create a project in Jira

First, let's create a project in Jira to manage code development.

In Jira, click on `Projects` in the top menu bar, then select `Create project` in the sub-menu.  This will open a "Create project" dialog.

In the dialog, click `Next`, then click `Select`.  Populate the form:
- Name: "Coffee Bar"
- Key: "CBR"

Click `Submit`.  The page will change to show the new project.

#### Create an issue in the project

Click the blue `Create` button in the top menu bar.  A form dialog will show up. Populate some of the fields:
- Project: Make sure the "Coffee bar" project is selected.
- Issue Type: Make sure "Story" is selected.
- Summary: Enter something like "Expand menu to include juice drinks" (or anything else you think you might to change in your code).
- Description: (optional) Add a description if you desire.

Click the `Create` button in the lower right of the dialog.  Your new issue ticket should show up in the project backlog.

### Create a branch from Jira

Click on the issue on the project backlog page.  This will open the issue details in a right panel.  Expand the issue details by clicking on the issue ticket number (e.g., `CBR-1`) at the top of the issue details panel.

In the issue details view, look for the "Development" subsection on the right.  Below that should be a `Create branch` link.  Click it.  The browser page will switch to the "Create Branch" page in Bitbucket.

Populate the fields for the new branch:
- Repository - Make sure the "Coffee Bar" repository is selected.
- Branch type - Leave as "Feature".
- Branch from - Select "Integration".
- Branch name - Keep the auto-populated branch name

Click the `Create branch` button.  The page will stay in Bitbucket and show the source code in the new branch.

In Bitbucket, click on `Branches` in the left menu panel.  In the shown list of branches, see the new branch and also see a link to the Jira issue on the right.

Go back to Jira.  You can either use the browser back button, or you can open a new browser tab and reenter the Jira URL.

Open the issue you had created in Jira.  You can find it by clicking on `Issues` in the top menu bar, then selecting your issue under "RECENT ISSUES" in the drop-down menu.

Notice that under the "Development" section on the right of the issue details page you will now see a link `1 branch`.  Click it to bring up a dialog showing some details for the branch.  Then close the dialog.

### Link a commit between Jira and Bitbucket

#### Create a commit in Bitbucket

Go to Bitbucket.

Click on `Source` in the left menu panel.  On the source page, change the selected branch to be the new feature branch.

Click on the `menu.txt` file name to open the file content, then click the `Edit` button.

Make a change to the content, then click the `Commit` button.  In the commit dialog, change the commit message to include a reference to the Jira ticket (e.g., "**CBR-1** - menu.txt edited online with Bitbucket").  Then click the `Commit` button.

Click `Commits` in the left menu panel.  Notice that your new commit shows up, and notice a link to the Jira issue to the right.

#### View commit from Jira

Go back to Jira.  Open the issue if it is not already open.  Notice that a new link `1 commit` appears under the "Development" section in the ticket.  Click the link to open a dialog with commit details.  Then close the dialog.

### Create a pull request from Jira

In the Jira ticket, click on the `1 branch` link to open a dialog with details on the branch.

In the dialog, to the right of the branch name, there should be a clickable link `Create pull request`.  Click it.  The browser page will switch to the "Create pull request" page in Bitbucket.

For the pull request, leave the source as your new branch.  Change the destination branch to "integration".  Then click `Continue`, then `Create`.

Notice that the Jira issue appears as a linked reference on the pull request page in Bitbucket.

Return to Jira (either using the back button, or by reentering the Jira URL in the browser address).

In Jira, open the issue if it is not already open.  Notice a new link `1 pull request` under the "Development" section.  Click the link to open a dialog with details.

That's it for this lab.
