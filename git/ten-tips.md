# 10 Git Commands You Should Know

Source:
[10 Git Commands You Should Know](https://towardsdatascience.com/10-git-commands-you-should-know-df54bea1595c)

## Inspecting Things

Let’s look at inspecting changes first.

* `git diff` - See all file changes locally. A file name can be appended to show changes for only one file.
* `git log` — See all commit history. Can also be used for a file with `git log -p my_file`. Enter `q` to exit.
* `git blame my_file` — See who changed what and when in my_file.
* `git reflog` — Show a log of changes to the local repository’s HEAD. Good for finding lost work.

Inspecting things with Git isn’t terribly confusing. In contrast, Git provides a plethora of options for removing and undoing commits and file changes.

## Undoing Things

`git reset`, `git checkout`, and `git revert` are used to undo the effects of changes to your repository. These commands can be tricky to keep straight.

`git reset` and `git checkout` can be used on both commits and individual files. `git revert` is used only at the commit level.

If you are just dealing with your own local commits that haven’t been merged into collaborative remote work, you can use any of these commands.

If you are working collaboratively and need to neutralize a commit in the remote branch, `git revert` is your tool.

Each of these commands can take a variety of options. Here are common uses:

* `git reset --hard HEAD` — Discard staged and unstaged changes since the most recent commit. Specify a different commit instead of `HEAD` to discard changes since that commit. `--hard` specifies that both the staged and unstaged changes are discarded. Make sure you don’t discard a commit from a remote branch that your collaborators are depending upon!

* `git checkout my_commit` — Discard unstaged changes since *my_commit*. HEAD is often used for *my_commit* to discard changes to your local working directory since the most recent commit. `checkout` is best used for local-only undos. It doesn’t mess up the commit history from a remote branch that your collaborators are depending upon! If you use checkout with a branch instead of a commit, `HEAD` is switched to the specified branch and the working directory is updated to match. This is the more common use of the checkout command.

* `git revert my_commit` — Undo the effects of changes in *my_commit*. `revert` makes a new commit when it undoes the changes. `revert` is safe for collaborative projects because it doesn’t overwrite history that other users’ branches might depend upon.

Sometimes you just want to delete untracked files in your local directory. For example, maybe you ran some code that created lots of different types of files that you don’t want in your repo. Oops. 😏 You can clean them in a flash!

* `git clean -n` — Delete untracked files in the local working directory. The `-n` flag is for a dry run where nothing is deleted. Use the `-f` flag to actually remove the files. Use the `-d` flag to remove untracked directories. By default files untracked by `.gitignore` will not be deleted, but this behavior can be altered.

Now that you know the tools for undoing things in Git, let’s look at two more commands to keep things orderly.

## Tidying Things

* `git commit --amend` — Add your staged changes to the most recent commit. If nothing is staged, this command just allows you to edit the most recent commit message. Only use this command if the commit has not been integrated into the remote master branch!

* `git push my_remote --tags` — Send all local tags to the remote repo. Good for versioning changes.