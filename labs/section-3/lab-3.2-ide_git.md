# Using IDE Git Integration

Lab Objectives:
- Connect to Bitbucket from your favorite IDE
- Push changes to Bitbucket from IDE
- Pull changes to IDE from Bitbucket

## Lab

**Each IDE is different in how to use Git, so this lab does not provide detailed instructions.  Instead it only suggests a sequence of activities to perform.**

#### Create a new local repository

Since most IDEs have a particular structure to projects, solutions, workspaces, etc., the repositories you already have in Bitbucket for prier labs won't be recognized as appropriate for your IDE.  Instead, you should create a new local project or copy an existing one to work with in your IDE.

Initialize your new local project as a Git repository.  Recall that you can use the `git init` command.

#### Create a new empty repository in Bitbucket

Go to Bitbucket, and create a new repository.  It will be an empty repository in Bitbucket.

#### Connect your local repository to Bitbucket

Your IDE should have a way to set the remote for your local repository.  Set the remote to the new Bitbucket repository.

Once you have the remote set, use your IDE to push your local repository contents to Bitbucket.


#### Make local commits and push to Bitbucket

Edit one or more files through your IDE.  Then use your IDE to stage the files and then commit the changes.  Then use your IDE to push the commit to Bitbucket.

Go to Bitbucket and comfirm the new commit shows up there.

#### Pull changes from Bitbucket

Go into Bitbucket and edit a file from within Bitbucket.  Commit the change within Bitbucket.

Go back to your IDE and fetch the changes from Bitbucket.  Verify that the new commit and changes show up in your IDE.
