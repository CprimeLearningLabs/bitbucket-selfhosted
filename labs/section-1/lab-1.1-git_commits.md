# Git Commands for Making Local Changes

Lab Objectives:
- Create a new repository
- Use Git commands to make and revise commits
- Use Git commands to explore commits
- Revert a commit

## Prerequisites

You should have Git installed on your local machine.  If you do not have Git installed, see the installation documentation at either:
* https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
* https://www.atlassian.com/git/tutorials/install-git

## Lab

### Create a new repository

On your local machine, create a temporary directory where you will be able to create additional subdirectories.  In a command terminal, go to that temporary directory.

Create a folder for your new repository &mdash; let's call the repository `coffeebar`.  Then go into the folder:
```
mkdir coffeebar
cd coffeebar
```

Now execute the following command to initialize the folder as a new (empty) Git repository:
```
git init
```

Notice that the folder now has a `.git` subdirectory.  Your folder is now a bonafide Git repository.

### Create a few commits

Create a new file `menu.txt` using your favorite text editor (Visual Studio Code, notepad, vi, Atom, etc.).  Add some initial content to the file (such as creative names of some coffee drinks), and save the file.
```
vi menu.txt
```
> In this guide, the examples use the "vi" editor.  You can use whatever editor you prefer.

Check the Git status of your workspace and notice that the file is untracked.
```
git status
```

Create another file `welcome.txt`, add some friendly content and save the file.
```
vi welcome.txt
```

Check the Git status again to see that you now have two untracked files.
```
git status
```

Add the files to the Git staging index, and then check the status again.  Notice that the files are now ready to be committed.
```
git add -A
git status
```

Commit the changes.
```
git commit -m "initial commit"
```

If you check the status again, you will see that there are no changes detected.  You can check the Git log to see your commit.
```
git status
git log
```

Let's do it again.  Make some changes to the content of `menu.txt`.  Then check the Git status.  You will see the file is 'modified' instead of 'untracked'.  Do you know why?
```
vi menu.txt
git status
```

Add the file to staging, commit it, and check your commit history to see you have two commits now.
```
git add menu.txt
git commit -m "Updated menu"
git log
```

In case you forget what change you made to `menu.txt`. you can use the diff command to see.  In the command below, substitute the second to last commit SHA from the log in place of '&lt;commit&gt;'. (`HEAD` is a git reference to the latest commit.)
```
git diff <commit> HEAD
```

### Undo a commit

Oops! Let's suppose you didn't really want to commit that change.  Let's revert the last commit safely.
```
git revert HEAD
```
> The revert command may open a text editor for you to provide the commit message for the revert commit.

Examine the `menu.txt` file to confirm the changes were undone.

Check the log history to see the revert commit.
```
git log
```

That's it for this lab.
