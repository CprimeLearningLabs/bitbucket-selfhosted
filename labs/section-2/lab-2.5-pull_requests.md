# Pull Requests

Lab Objectives:
- Set repository settings for pull requests
- Create a pull request
- Review and approve a pull request
- Merge a pull request

## Prerequisites

You should have completed Lab 2.4.

## Lab

### Set repository settings for pull requests

Go to the "Bitbucket Lab" repository.

Click on the `Repository settings` menu item in the left menu panel.

#### Set merge checks

Click on the `Merge checks` menu item in the Repository settings menu panel.

All of merge checks should show as inherited from the project settings as disabled.  Let's change a couple:
- Change "Minimum approvals" to `enabled`, and in the pop-up dialog set the number of approvals to 1.
- Change "No 'needs work' status" to `enabled`.

#### Set allowed merge strategies

Click on the `Merge strategies` menu item in the Repository settings menu panel.

Notice that all the settings are not editable on the page.  To override the project settings, change the radio button under "Project settings inheritance" to the "Use custom settings" selection. The settings on the page then become editable.

The "Merge commit" strategy should already be enabled and set as default.  Let's allow a couple others:
- Enable "Rebase and merge" (don't set as default)
- Enable "Squash" (don't set as default)

Click `Save` at the bottom of the page.

#### Set default reviewer

Click on the `Default reviewers` menu item in the Repository settings menu panel.  Then click on the blue `Add default reviewers` button in the middle of the page.  This will open a dialog to set reviewer rules for branches.

In the dialog, populate the fields:
* Source branch - Select the "Any branch" radio button.
* Target branch - Select the "Branching model" radio button, then select "Production" in the drop down list.
* Default reviewers - Type "Jor" in the text box, and select the suggested user "Jordan".
* Approvals required - Leave as 0 since we set approvals in the merge checks.

Click the `Create` button.  The page will then show a summary of the added review rule.

### Create a pull request

Click on the `Create pull request` menu item in the left menu panel.  This will open a wizard for creating a pull request.

For the Source branch, select "feature-1ab-2.3".  Leave the Destination as "main".  Click the blue `Continue` button.

The next page is a pull request form.  We will accept all the default entries.  The description is a summary of the commits in the pull request.  The reviewers automatically includes "Jordan" by default just as we configured above.  Notice that if you try typing your own assigned name into the reviewers text box, you will not be able to add yourself as a reviewer.

The "Diff" and "Commits" sub-tabs show the changes to be merged by this pull request.

Click the blue `Create` button to save the pull request.  The resulting page shows the created pull request.

Notice in the upper right of the page that the pull request is blocked pending approval.

Click on the `Pull requests` menu item in the left menu panel.  See that your pull request is listed as an open pull request.

### Review and approve the pull request

Open a second browser tab or window, and log into Bitbucket as user "Jordan".  The class instructor should have provided you with credentials for that user.

After logging in as Jordan, you will notice the new pull request listed as pending your review.

#### Review the pull request

As user Jordan, click on the pull request link from the dashboard page. (If you have clicked around, you can get back to the dashboard page by clicking on the Bitbucket logo in the upper left corner of the page.)

On the pull request page, notice that the `Needs work` and `Approve` buttons appear in the upper right.

Click on the `Diff` sub-tab to show the changes to the files affected by the pull request.  Let's add some comments.

Click on the `Start review` button in the upper right of the page.  This will prevent publishing your comments into the Overview section until you are done with the review.

Hover over a green highlighted line in `afile.txt` and click the blue `+` icon that appears.  Add a comment and then click `Add comment`.

Hover over a green highlighted line in `readme.md` and click the blue `+` icon that appears.  Add a comment and then click `Convert to task`.

Click the `Finish review` button in the upper right of the page.  This will open a dialog to finalize the review.
* Add an overview comment.
* Select the "Needs work" radio button.

Click `Publish` in the dialog.  

Click on the `Overview` sub-tab to see the published review comments.  Notice the changes to the pull request review status in the upper right: there are now two merge blockers, and there is a pending open task.

#### Resolve a merge block

Go back to the browser tab or window in which you were logged in as "Student" user.

Click on the `Pull requests` menu item in the left menu panel to open a list of pull requests.  Then click on the name link of the listed pull request.

Scroll through the comments shown on the `Overview` sub-tab.  Reply to  one or more of the comments.

Click on the `1 open task` button at the top of the page.  Click the checkbox to resolve the task.  Notice that the number of merge blockers is reduced on the pull request page.  There is still a blocker that approval is pending. You cannot approve your own pull request.

#### Approve the pull request

Go back to the browser tab or window in which you were logged in as "Jordan" user.

Refresh the pull request page to get the updates from the changes above.

In the upper right of the page, click on the green checkmark icon to approve the pull request.  Notice that the `Merge` button becomes enabled.

### Merge the pull request

Still as user Jordan, click the `Merge` button.  

A merge dialog appears with a number of fields:
* Commit message - The top text box is the commit summary.  The lower text box is additional commit message content.  We will accept the suggested content.
* Source branch deletion - Recall that we earlier set that source branches should be deleted by default on pull request merges.  We could override that default, but leave it checked.
* Merge strategy - Next to the `Merge` button is a drop-down with allowed merge strategies.  Again, we will keep with the default "Merge commit" strategy.

Click the `Merge` button.  The pull request status should change to `MERGED`.

Click the `Commits` menu item in the left menu panel to show all the commits for the main branch.  Confirm that the pull request merge commit appears.

Click the `Branches` menu item in the left menu panel to show a list of branches.  Confirm that the "feature-lab-2.3" brand is no longer present.

Finally, log out of the window for Jordan.  Jordan's work is done for today.
