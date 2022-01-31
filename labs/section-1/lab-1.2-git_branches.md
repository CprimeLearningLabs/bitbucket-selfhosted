# Git Commands for Working with Branches

Lab Objectives:
- Create a new branch
- Commit changes on a branch
- Merge two branches
- Use Git stash to set aside changes when switching branches
- Handle a merge conflict

## Prerequisites

You should have done Lab 1.1 prior to this lab.

## Lab

### Create a new branch

On your local machine, go to the repository you created in lab 1.1.

Let's check what branch you are on currently. The `git status` command will tell you.  Confirm you are on the 'master' (or 'main') branch.
```
git status
```

Create a new branch.
```
git branch feature-one
```

If you type `git status` again, you will see you are still on the 'master' (or 'main') branch.
```
git status
```

To see that you created a new branch, use the `git branch` command with the '-a' option. Your current branch will be preceded by an asterisk.
```
git branch -a
```

Switch to the new branch, and retry either (or both) the `git status` and `git branch -a` commands to confirm you are on the new branch.
```
git switch feature-one
git status
git branch -a
```

Look at the history of commits on the branch.  Notice that the branch includes commits carried over from the original branch.  Also notice that HEAD points to the tip of the new branch.
```
git log --oneline
```

### Make changes on the new branch

Let's make some changes on your new branch.  

Make changes to `menu.txt` and commit the changes.
```
vi menu.txt
git add .
git commit -m "feature-one changes to menu"
```

Now make changes to `welcome.txt` and commit those changes.
```
vi welcome.txt
git add .
git commit -m "changes to welcome.txt on feature-one branch"
```

Take a look at your commit history now.  See that both HEAD and the branch ref have the new commits in their history.
```
git log --oneline
```

**QUESTION:** *If you were to do a merge of your feature branch to the master branch right now, would you do a fast-forward merge or a non-fast-forward merge?  Why?*

### Merge the feature branch to master

To perform a merge, we need to switch to the target branch, which is 'master' (or 'main').
```
git switch master
```

We can now merge the feature branch into master.  We will do the merge with a merge commit even though a fast-forward merge is technically possible.
```
git merge feature-one --no-ff -m "Merge feature-one to master"
```
> If you did not include the '-m' option, then git will automatically open up a text editor for you to write a commit message.

Check the commit history to confirm the merge happened. We use the graph option to nicely show the branching and merge.
```
git log --oneline --graph --all
```

### Use Git stash

Let's consider the case where you make a change on a feature branch, but need to switch to another branch without first committing the change.  Let's see how it would work.

Go back to your feature branch, make a change to the &ast;**first line**&ast; in the `menu.txt` file.  Add the change to the staging index, but don't commit.  Executing `git status` should show that the file is only modified.
```
git switch feature-one
vi menu.txt
git add -A
git status
```

Switch to the 'master' branch and run git status.
```
git switch master
git status
```

Notice that the uncommitted change from the feature branch shows up in the status for the master branch.  But you don't want this change in master yet.  We'll need to use git stash to temporarily put the change aside.  Go back to the feature branch and run git stash.  Then check the git status.
```
git switch feature-one
git stash push
git status
```

The changes no longer appear in git status.  So you can safely switch to the master branch and commit a separate change to the `menu.txt` file.  Make a change to the &ast;**first line**&ast; of text in that file and commit it.
```
git switch master
vi menu.txt
git add -A
git commit -m "edited menu on master branch"
```

Now return to the feature branch, unstash the prior change to `menu.txt`.  Notice that the prior stashed changes have been restored in your working directory.
```
git switch feature-one
git stash pop
git status
```

Commit the change to `menu.txt` on your feature branch.
```
git add -A
git commit -m "menu edit after un-stash on feature-one"
```

### Handling a merge conflict

Look at your commit history.  You will notice at this point that there are changes to `menu.txt` on both the feature branch and master branch.  
```
git log --oneline --graph --all
```

We would like to merge the feature branch to the master branch, but there will be a merge conflict due to incompatible changes in the first line of `menu.txt`.  Merging the feature branch to the master branch would result in a "corrupted" file in the production master branch.  The better solution is to resolve the merge conflict in the feature branch first.

Merge the master branch into the feature branch.  Since we are already on the feature branch, we can just execute the merge command.
```
git merge master -m "Merge master to feature-one to resolve menu issues"
```

The merge should have produced a message that Git detected a merge conflict.  You'll need to manually resolve the conflict.  Open `menu.txt` to see what Git has done there.  Notice the markers for the conflicting changes.  Edit the file to resolve the conflict &mdash; *be sure to remove the special markers as well*.
```
vi menu.txt
```

You can now complete the merge. You'll need to first add the file to the staging index, then resume the merge.
```
git add menu.txt
git merge --continue
```
> Note: You could have alternatively done a 'git commit' in place of the 'git merge --continue'.

Look at the commit graph to see what you have done.
```
git log --oneline --graph --all
```

With the merge conflict resolved, you can now confidently merge the feature branch to the master branch.
```
git switch master
git merge --no-ff feature-one -m "Merge feature-one into master"
```

Look at the commit graph again to see the results.
```
git log --oneline --graph --all
```

**QUESTION:** *An alternative to merging the master branch into the feature branch would have been to rebase the feature branch onto the master branch.  What would be the advantage and disadvantage of doing the rebase instead of the merge?*
