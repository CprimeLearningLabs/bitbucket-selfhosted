# Repository Settings

Lab Objectives:
- Set repository permissions
- Set branch protection
- Set branching model

## Prerequisites

You should have completed Lab 2.3.

## Lab

### Set access permissions

We will set access permissions at the project level first, and then extend the permissions at the repository level.

In Bitbucket, go to the "Training Labs" project.  

Click on the `Project settings` menu item in the left menu panel. Then click on the `Project permissions` menu item in the Project settings menu panel.

Notice that as the project creator, you are already granted access at the "admin" level.  Let's grant access to all developers.

In the "Add Groups" field under the "Group access" heading, type in "Dev" and see that "Developers" is an auto-suggested user. Select "Developers".  To the right, select "Write" as the level of permission to grant.  Then click the `Add` button.

Now go to the "Bitbucket Lab" repository.  (Remember, a quick way to get to a repository is from the `Repositories` top menu drop down.)

Click on the `Repository settings` menu item in the left menu panel.  Then click on the `Repository permissions` menu item in the Repository settings menu panel.

Don't worry that you don't see your name or the Developers group listed as granted access.  The repository permissions extend what you already set at the project level.  We are going to increase the permission level of a developer named Jordan just for this repository.

In the "Add users" field under the "User access" heading, type in "Jor" and select "Jordan".  To the right, select "Admin" as the level of permission to grant.  Then click the `Add` button.

### Set protections on the main branch

Locking down the production branch is always a good idea.  Let's do it at the project level so the protection automatically applies to all repositories in the project.

Go to the "Training Labs" project.  

Click on the `Project settings` menu item in the left menu panel. Then click on the `Branch permissions` menu item in the Project settings menu panel.  Then click on the blue `Add permission` button in the middle of the page.  This will open a dialog to set a branch permission.

In the dialog, populate the fields:
* Branches - Leave the "Branch name" radio button selected, and enter "main" as the branch name.
* Restrictions - Check the "Prevent all changes" checkbox and the "Prevent changes without a pull request" checkbox.  As exceptions to "Prevent all changes", enter the name "Jordan" and your assigned student name. (If you forget your assigned student name, cancel the dialog and hover your mouse over the user avatar in the upper right corner of the page.)  Don't enter any exceptions for the pull request restriction.

Click the `Create` button.  The page will then show a summary of the added branch protections.

### Set branching model

Let's now modify the branching model just for the "Bitbucket Lab" repository.

Go to the "Bitbucket Lab" repository.

Click on the `Repository settings` menu item in the left menu panel.  Then click on the `Branches` menu item in the Repository settings menu panel.

Notice that all the settings are disabled on the page.  To override the project settings, change the radio button under "Project settings inheritance" to the "Use custom settings" selection. The settings on the page then become enabled.

#### Branching model

Leave the Development radio selection unchanged.

For the Production radio selection, choose "Use branch name", and then select "main" as the production branch.

#### Branch prefixes

We will be creating only feature branches in this repository.

Uncheck "Bugfix", "Hotfix", and "Release".  For "Feature", change the prefix to "feature-".

#### Automatic merging

We will leave the settings unchanged, with automatic merging "Off".

#### Branch deletion on merge

Pruning unnecessary branches is a good idea.  Change the Default to "On".  (This can be overridden at the time of a merge.)

Click the blue `Save` button at the bottom of the page.
