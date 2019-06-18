#                                                                      TASK-1

**1.What is VCS? and Why it is important?**

Version control is important for today’s development teams. It needs to do more than just manage and track files. It should help you develop and ship products faster. This is especially important for teams practicing DevOps.

VCS is important as it improves visibility,helps teams collaborate around the world and accelerates product delivery

**2.How to clone a Git repository?**

When you create a repository on GitHub, it exists as a *remote* repository. You can clone your repository to create a *local* copy on your computer and sync between the two locations.

This procedure assumes you have already [created a repository on GitHub](https://help.github.com/en/articles/creating-a-new-repository), or have an existing repository owned by someone else you'd like to contribute to.

1. On GitHub, navigate to the main page of the repository.

   **Note:** If the repository is empty, you can manually copy the repository page's URL from your browser and skip to step four.

2. Under the repository name, click **Clone or download**. 

   ![Clone or download button](https://help.github.com/assets/images/help/repository/clone-repo-clone-url-button.png)

   

3. In the Clone with HTTPs section, click  to copy the clone URL for the repository. 

   ![Clone URL button](https://help.github.com/assets/images/help/repository/https-url-clone.png)

   

4. Open Git Bash.

5. Change the current working directory to the location where you want the cloned directory to be made.

6. Type `git clone`, and then paste the URL you copied in Step 2.

   ```shell
   $ git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY
   ```

7. Press **Enter**. Your local clone will be created.

   ```
   $ git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY
   > Cloning into `Spoon-Knife`...
   > remote: Counting objects: 10, done.
   > remote: Compressing objects: 100% (8/8), done.
   > remove: Total 10 (delta 1), reused 10 (delta 1)
   > Unpacking objects: 100% (10/10), done.
   ```

   **3.How to pull/push to remote repository?**

Pushing to the remote for the first time

When you push your files onto the remote for the first time, make sure the create tracking reference checkbox is checked.

![img](https://cdn-images-1.medium.com/max/800/0*AMl2y-GbAIyidZf6.png)

A tracking reference tells Git to track the current branch (master in this case) and to push or pull to the same branch on the remote.

If you don’t create a tracking reference, you will need to specify which branch to push to (or pull from) every time.

Once that is checked, you can click push and Fork will push your project onto Github.

Once it is pushed, you can look at the All Commits section. (In other Git clients, that will be Git History).

In all commits, you’ll see two tags. One is called `master` (the master branch on our computer). And the other is called `origin/master` (the master branch on the remote named origin). In this case, our origin is Github, so `origin/master` refers to the master branch on Github.

![img](https://cdn-images-1.medium.com/max/800/0*0S0Dsq457t6SlO-9.png)

When these two tags are on the same commit, it means the files we have on our local master branch is the same as the files we have on Github’s master branch.

You can verify this is true if you go back to the page where you got the Git remote URL from. Refresh this page and you’ll see what you’ll usually see on Github (a project page).

![img](https://cdn-images-1.medium.com/max/800/0*kiR9rIjqnxBBq4hg.png)

If you look at the files, you’ll notice that the files are exactly the same as the files you have on your computer.

**4.How to check the status of the repository?**

Use the `git status` command, to check the current state of the repository.  

#### Run:

```
git status
```

  You will see

#### Result:

```
$ git status
# On branch master
nothing to commit (working directory clean)  
```

The command checks the status and reports that there’s nothing to commit, meaning the repository stores the current state of the working directory, and there are no changes to record.  

We will use the git status, to keep monitoring the states of both the working directory and the repository

**5.How to create and switch to a branch?**

We can use below command

| 01234 | git checkout –b <branchname> |
| ----- | ---------------------------- |
|       |                              |

So this command will do both the two things one is it will create a new branch and it will switch to that branch.



![git create and switch to branch](https://www.decodingdevops.com/wp-content/uploads/2018/10/git-create-and-switch-to-branch.jpg)

 

You can see in the image that I created branch name called sony and I switched to that branch with this single command. So this command will useful only when you are creating a new branch. But to switch to any existed branch we use  normal git checkout command.

**6.How to connect to a remote a repository?**

As an example in Gittower clients, we'll connect a remote from GitHub (at the URL "<https://github.com/gittower/git-crash-course-remote.git>") and call it "origin":
 With the local repository open in Tower, click the "+" button on the bottom of the toolbar and select "Add Remote Repository...". In the following dialog, you can enter your authentication details for this remote.

 

![img](https://www.git-tower.com/learn/content/01-git/01-ebook/en/02-desktop-gui/04-remote-repositories/02-connecting-remote-repositories/01-remote-add_windows.gif)

 

Note that you can connect as many remotes with a local repository as you like.

**7.How to merge two branch?**

`merge` command is used to bring two (or more) branches together.  

 Example:

```
# on branch A:
# create new branch B
$ git checkout -b B
# hack hack
$ git commit -am "commit on branch B"

# create new branch C from A
$ git checkout -b C A
# hack hack
$ git commit -am "commit on branch C"

# go back to branch A
$ git checkout A
# hack hack
$ git commit -am "commit on branch A"
```

so now there are three separate branches (namely A B and C) with different heads

to get the changes from B and C back to A, checkout A (already done in this example) and then use the merge command:  

```
# create an octopus merge
$ git merge B C
```

  your history will then look something like this: 

```
…-o-o-x-------A
      |\     /|
      | B---/ |
       \     /
        C---/
```

**8.How to resolve merge conflicts?**

General Tools used:

```
git status 
```

The status command is in frequent use when a working with Git and during a merge it will help identify conflicted files.

```
git log --merge
```

Passing the `--merge` argument to the `git log` command will produce a log with a list of commits that conflict between the merging branches.

```
git diff
```

`diff` helps find differences between states of a repository/files. This is useful in predicting and preventing merge conflicts.

**9.How to commit changes?**

Remember that anything that is still unstaged — any files you have created or modified that you haven’t run `git add` on since you edited them — won’t go into this commit. They will stay as modified files on your disk. In this case, let’s say that the last time you ran `git status`, you saw that everything was staged, so you’re ready to commit your changes. The simplest way to commit is to type `git commit`:

```console
$ git commit 
```

Doing so launches your editor of choice. (This is set by your shell’s `EDITOR` environment variable — usually vim or emacs, although you can configure it with whatever you want using the `git config --global core.editor` command as you saw in [Getting Started](https://git-scm.com/book/en/v2/ch00/ch01-getting-started)).

The editor displays the following text (this example is a Vim screen):

```
# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
# On branch master
# Your branch is up-to-date with 'origin/master'.
#
# Changes to be committed:
#	new file:   README
#	modified:   CONTRIBUTING.md
#
~
~
~
".git/COMMIT_EDITMSG" 9L, 283C
```

You can see that the default commit message contains the latest output of the `git status` command commented out and one empty line on top. You can remove these comments and type your commit message, or you can leave them there to help you remember what you’re committing. (For an even more explicit reminder of what you’ve modified, you can pass the `-v` option to `git commit`. Doing so also puts the diff of your change in the editor so you can see exactly what changes you’re committing.) When you exit the editor, Git creates your commit with that commit message (with the comments and diff stripped out).

 Alternatively, you can type your commit message inline with the `commit` command by specifying it after a `-m` flag, like this:

```console
$ git commit -m "Story 182: Fix benchmarks for speed"
[master 463dc4f] Story 182: Fix benchmarks for speed
 2 files changed, 2 insertions(+)
 create mode 100644 README
```

Now you’ve created your first commit! You can see that the commit has given you some output about itself: which branch you committed to (`master`), what SHA-1 checksum the commit has (`463dc4f`), how many files were changed, and statistics about lines added and removed in the commit.

Remember that the commit records the snapshot you set up in your staging area. Anything you didn’t stage is still sitting there modified; you can do another commit to add it to your history. Every time you perform a commit, you’re recording a snapshot of your project that you can revert to or compare to later.

**10.How to stash changes?**

The "git stash" command can help you to (temporarily but safely) store your uncommitted local changes - and leave you with a clean working copy.

git stash: a Clipboard for Your Changes

Let's say you currently have a couple of local modifications:

```
$ git status
  modified:   index.php
  modified:   css/styles.css 
```

If you have to switch context - e.g. because you need to work on an urgent bug - you need to get these changes out of the way. You shouldn't just commit them, of course, because it's unfinished work. 

This is where "git stash" comes in handy:

```
$ git stash
Saved working directory and index state WIP on master:
   2dfe283 Implement the new login box
HEAD is now at 2dfe283 Implement the new login box
```

Your working copy is now clean: all uncommitted local changes have been saved on this kind of "clipboard" that Git's Stash represents. You're ready to start your new task (for example by pulling changes from remote or simply switching branches).