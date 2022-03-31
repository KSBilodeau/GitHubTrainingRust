
# Rust Training Track

This branch is dedicated to the basics of using GitHub in conjunction with Rust!  For those with minimal experience with Rust and wanting to learn more, please consult the official [Online Rust Book](https://doc.rust-lang.org/book/).

## Table of Contents

##### Day 1:

1. [Lesson 1 - Forking a project]()
2. [Lesson 2 - Cloning a project]()
3. [Lesson 3 - Making commits]()
   1. [Lesson 3a - Amending a commit]()
   2. [Lesson 3b - Reverting a commit]()
4. [Lesson 4 - Pushing a commit]()

##### Day 2:

1. [Lesson 5 - Opening issues]()
2. [Lesson 6 - Creating branches]()
3. [Lesson 7 - Making pull requests]()
4. [Lesson 8 - Resolving issues]()

## Lesson 1 - Forking a Project

When you fork a repository, you are making a copy of a person's project for you to edit and push changes to.  This will then allow you to make pull requests to repositories you do not personally own.  Follow these steps to make a fork of this repository:

##### Step 1 - Navigate to the Repository Page:

To begin go to [this repositories page](https://github.com/KSBilodeau/GitHubTrainingRust) (if you are not there already).  It should look like this:

[![](https://gcdnb.pbrd.co/images/nYUwzT51TcBE.png?o=1)](https://gcdnb.pbrd.co/images/nYUwzT51TcBE.png?o=1)

##### Step 2 - Click the Fork Button

Then simply click the fork button as you can see as follows:

[![](https://gcdnb.pbrd.co/images/UTLhXcBh53kn.png?o=1)](https://gcdnb.pbrd.co/images/UTLhXcBh53kn.png?o=1)

You should now see the repository in your repository list:

[![](https://gcdnb.pbrd.co/images/sQ3jZibLNBXV.png?o=1)](https://gcdnb.pbrd.co/images/sQ3jZibLNBXV.png?o=1)


## Lesson 2 - Cloning a project:

Cloning is used for grabbing a repository from some remote location and downloading locally.  This is helpful when contributing to projects you do not own; however, it is also great in the case you mess up your local files and require a download of a backup. Follow the directions as follows to clone this repository locally:

##### Step 1 - Open the terminal:

Simply open the terminal and cd to where you would like to have the repo stored.  Note that the final command will make a folder to enclose any downloaded materials, so there is no need to create an enclosing folder.

##### Step 2 - Copy the clone link:

Navigate to the repository page and click the green code button.  Then copy the url under the https section, like as follows:

[![](https://gcdnb.pbrd.co/images/Auzyas2IWXLw.png?o=1)](https://gcdnb.pbrd.co/images/Auzyas2IWXLw.png?o=1)

##### Step 3 - Run the git clone command:

Run the following command and it should download the files:

```bash
git clone INSERT_CLONE_URL_HERE
```

## Lesson 3 - Making commits:

To make a commit, you must first add the files to be staged like so:

```bash
git add .
```

Then you must do the following two commands (assuming that you have already added your ssh key):

```bash
git commit -m "DESCRIBE YOUR COMMIT HERE"
git push
```

##### Lesson 3a - Amending a commit:

Say you made a typo or a mistake when typing the message during your last commit.  In order to fix it, simply commit again but using the --amend flag like so:

```bash
git commit --ammend -m "DESCRIBE YOUR COMMIT HERE PROPERLY"
git push
```

If you forgot a file or even forgot to add any files, simply use the add command before amending (you can leave off the -m if the message was correct):

```bash 
git add MISSING_FILE
git commit ---ammend
git push
```

##### Lesson 3b - Reverting a Commit:

To reset your code to the exact state it was at the last commit, you can use git revert!  Thankfully, this version creates a commit to revert the commit so history is preserved and you dont have to worry if you make a mistake.  Use the command like so:

```bash
git revert --no-commit STARTING_COMMIT_HASH..HEAD
git commit
```

###### Quick Tip - Finding Commit Hashes:

Use the `git log` command to quickly find the hashes of every commit you have made like so:

```bash
git log
```

###### Dangerous Tips - Changing Git Log History:

To revert your code to the exact state it was before you committed even in the history, you can use the reset command with the --soft flag (this is a bit harder to undo, and can be impossible if the reverted commit is removed from the git cache). This will ensure your files are left as they are but the commit history is back to where it was before like so:

```bash
git reset --soft HEAD~1
```

To reset your code to the exact state it was at the last commit, you can use the reset command's --hard flag. **WARNING THIS WILL DELETE CHANGES PERFORMED AFTER THE LAST COMMIT** (commit can be retreived in the case of emergency though):

```bash
git reset --hard HEAD~1
```

If you want these changes in history to be reflected on the online repository, you will need to force push:

```bash
git push -f
```

## Lesson 4 - Pushing Commits:

As you saw before, there are two ways to push a commit (for the purposes of this tutorial).  You can either force push or normal push like so:

```bash
git push
# or 
git push -f
```

Force pushing is only to be used in cases where you are sure you know what you are doing and generally for overwriting git history on the online repository.  Normal pushes are safer and keep the commit history in mind to ensure you do not cause any conflicts between the online repository and your local repository.


In the case there is a disconnect between the two, you can always try `git fetch` to get the latest version of the repo like so:

```bash
git fetch
```