# Git

Have you ever worked on an essay and ended up with the following kinds of files?

```
term_paper_draft2_edits.doc
term_paper_final.doc
term_paper_final_final.doc
term_paper_final_for_real_final.doc
```

Why did you create so many versions of your essay? It's likely because you had to make big changes, but you also didn't want to lose your previous version. You wanted to have that old version as a reference or if things went really poorly, to be able to go back and use the old version.

`git` is a version control system (VCS), that elegantly handles different versions of your code and let's you move back and forth through history of your work. So you don't have to have so many files like you might have had with your essays. It is also designed to allow for seamless collaboration with others.

`git` uses a different strategy for saving your code, so it will take a little bit of time to get used to using it.

## Learning Objectives

- Understand what _Git_ is and why it is vital to the development process.
- Create a git repository.
- Learn some basic git commands

<hr>

## Framing & Background

A **version control system** (or VCS) provides an automatic way to track changes in software projects. This system gives creators the power to view previous versions of files and directories. It also lets them develop new features without disrupting the work codebase.

Additionally, it can securely back up the project and its history. And it allows creators to collaborate efficiently and conveniently with each other. Think of it like the "Save" feature on a local document, except every time you click "Save", you create a snapshot of your project that you can return to or share with others anytime.

Additionally, version control also makes deploying production websites and web applications much more effortless. We (and most developers) use the version control system called **Git**. Git is an open standard that lets individual developers and large organizations manage a project as it changes over time.

Unlike pressing the save button for a file, `git` requires three steps:

- Choosing which files to `save`. This is called `staging` and is used with the command `add`. Within a project, you may only want to save one file, a few, or all.
- Saving the files. This is called `committing` and is used with the command `commit`
- Adding a `commit message`. Each time you save (or commit) your files it is expected that you explain what the change is. This essential for you to look back at previous version of your code and find the version you want.

## Getting started

The most common way to use Git is via a command-line program called `git`, which lets us transform an ordinary folder into a repository (or `repo`, for short) that enables us to track changes to our project.

The easiest way to check for Git is to start a terminal window and use `which` at the command line to see if the git executable is already present:

```bash
$ which git
/usr/local/bin/git
```

If the result is empty or the command is not found, you have to install Git, please refer to your computer setup guide to complete the necessary steps.

### Set Your Identity

You will want your name and email associated with all of your work. Take a few moments to configure this.

Test if you have your email set by running `git config --global user.email` in
your terminal. Hopefully, you see the output of what your email is set to.

If it's blank, type `git config --global user.email "example@email.com"` (where "example" is your GitHub account's associated email) to set it.

Do the same with your name. Run `git config --global user.name` and see if it's set. If not, set it.`

You will only ever need to run this once. Git will always use this information for anything you do on your computer.

## Initializing a Repo

We’ll begin by making a directory with the name `git-test` which will be the top level folder for a project. To make a directory or folder, we use the command `mkdir`, which is short for _**m**a**k**e **dir**ectory_. Then you will run the command `cd git-test`, which _**c**hanges **d**irectory_ (or folder) to the git-test folder we just created. Then we're going to make a readme file. `.md` is the suffix for a `markdown` file which is a type of text file.

```bash
$ mkdir git-test
$ cd git-test
$ touch README.md
```

Now that we're in the folder, we will turn it into a `repository`. A Git repository, or "repo", represents a single project managed via Git. The way to create a new repository with Git is with the `init` command (short for _initialize_), which makes a special hidden directory where Git stores the information it needs to track our project’s changes.

> **Note**: It is critical to not put a git repository inside another git repository. This will lead to problems tracking your code.

To confirm that a directory is NOT a `git` repository:

```bash
$ git status
# fatal: not a git repository (or any of the parent directories): .git
```

The word `fatal` seems intense, but it is ok. For us, this means it is ok to create the current directory into a git repository.

```bash
$ git init
# Initialized empty Git repository in /Users/jabyess/git-test/.git/
```

We now have a boilerplate Git repo to store our files and track their changes over time!

> You can see the `.git` folder by doing `ls -a` in your project directory. This is where all the git history lives. If you delete this folder, you will delete all your git history.

## Initial Commit

We can check the status of our Git repo by typing `git status`. This will tell us which files have changed since we last updated our Git repo. Check out what happens when we type `git status`:

![001](assets/001.png)

We see here that the README.md file is “untracked”, meaning git isn't paying attention to its contents. We can add it using the `git add` command:

```bash
$ git add README.md
```

We can add individual files by specifying them by name/filepath, or we can add an entire folder by doing:

```bash
$ git add .
```

Here the `.` tells Git to add **all** untracked files (and folders) from the current folder to the repo, thereby updating the status of each file in the repo. Now if we write `git status` again:

![002](assets/002.png)

As implied by the word _unstage_, the status of the file has been promoted from untracked to _staged_, which means the file is ready to be _committed_ to the repository. Untracked and staged are two of the four states commonly used by Git.

![git status sequence](assets/git_status_sequence.png)

After adding changes in the staging area, we can make them part of the local repository by _committing_ them using `git commit`. We should also add the command-line option `-m` to include a message indicating the purpose of the commit. **Commit messages are essential because it tells your collaborators what you changed!** They should be short and precise. The preference for commit message is **present-tense**, imperative-style. Examples of verbs to use: create, merge, update, delete, refactor, extract, fix

For our example, the purpose is to initialize the new repository, which we can indicate as follows:

```bash
$ git commit -m "initialize repo"
[master (root-commit) 38aeeb2] initialize repo
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
```

Now our changes are saved locally to our computer. All we've done is commit an empty file, but we're off to a good start!

At this point, we can use `git log` to see a record of our commit:

```bash
$ git log
commit 38aeeb24b51e4a01a61e1095e1f0efe38b137104
Author: lizraeli <leo2002b@yahoo.com>
Date: Tue Oct 3 18:40:20 2017 -0400

 initialize repo
```

The commit is identified by a unique string of letters and numbers that Git uses to label the commit, which lets Git retrieve the commit’s changes.

### Viewing the diff

It’s often helpful to view the changes a potential commit represents before making. To see how this works, let’s open the folder in VSCode:

```bash
$ code .
```

Open `README.md` and write `hello, world` in it.

Then type `git diff` to see the changes.

Git shows the difference between the last commit and unstaged changes in the current project:

![003](assets/003.png)

> The + indicates a line was added and shows the contents of the line.

We can commit this change by again adding the file and then committing.

```bash
$ git add README.md
$ git commit -m "add content to readme"
[master 092beb2] add content to readme
 1 file changed, 1 insertion(+)
```

Having added and committed the changes, there’s now no diff:

```bash
$ git diff

```

Simply adding the changes is sufficient; running `git add -a` would also lead to there being no diff. To see the difference between staged changes and the previous version of the repo, use `git diff --staged`.

We can confirm that the change went through by running `git log`:

![004](assets/004.png)

### Adding a Markdown tag

Adding a `#` before the text `hello world` will cause it to appear as a header:

```markdown
# hello, world
```

As before, we’ll run git status and git diff to learn more about what we will commit to Git. The status indicates that `README.md` has been modified:

![005](assets/005.png)

Meanwhile, the diff shows that one line has been deleted (indicated with -) and another added (indicated with +):

![006](assets/006.png)

At this point, we’re ready to add and commit to our changes.

```bash
$ git add README.md
$ git commit -m "Add a # tag"
[master ea24eb6] Add a # tag
 1 file changed, 1 insertion(+), 1 deletion(-)
```

### Adding a line of text

Let's add a blank line followed by our name to `README.md`:

```markdown
# Hello, world

My name is Lev
```

As usual, we can see the changes represented by our addition using `git diff`:

![007](assets/007.png)

### Git log

The `git log` command can show the entire commit history of our repo. For each commit, it will show its id, the author, the date, and the commit message. To limit the number of commits, we can add the flag `-[number]`: this will show the provided number of commits, from newest to oldest. Press `q` to `q`uit the view.

![011](assets/011.png)

Sometimes it's helpful to have a shorter overview. Another way to view logs is to run `git log --oneline`

The critical thing to notice here is the long string of characters after the word `commit`. This is called the **commit sha** (**s**imple **h**ashing **a**lgorithm), a unique identifier for each commit.

```
commit aba9ad9ae8d8ff6a23a10a691f690f7934d47986
```

We'll use the commit `sha` in a later step.

## Git reverts

One fundamental philosophy of git is that it's **append only**. This means you can't delete a commit because that would be deleting some of the project's history.

We have an option in case you want to _undo_ something previously committed, which is the `revert` function.

A `revert` is another commit that does the opposite of a commit. So if you added 4 lines and removed 2, a revert would remove those 4 lines and add 2.

When doing a revert, you must tell git which commit to revert. This is where `git log` and the `commit sha` come in handy.

Steps to revert:

- Make sure you don't have any uncommitted changes.
- `git log` to see the commits and associated `sha`s
- Copy the entire sha of the commit you want to revert
- `git revert <sha>`
- Enter a commit message. Close the window in that you wrote the message.
- Your revert should be done! Check the contents of the files to see if the changes are there.

## Exiting Vim

Vim is a text editor in terminal. It is typically the default text editor that git uses. The original version of Vim was made in the 1970s before computers had mice/trackpads so all the commands and navigation were done through a keyboard. To use Vim, you must learn the keyboard commands.

Occasionally, git will open Vim so you can add additional details to a commit. Exiting Vim is not intuitive, you must press `:wq` (**w**rite, **q**uit) to exit out of Vim with git correctly.

## Resources

- [Git tutorials](https://www.atlassian.com/git/tutorials)
- [Git cheatsheet](http://ndpsoftware.com/git-cheatsheet.html)
- [Git flight rules](https://github.com/k88hudson/git-flight-rules)
- [Try Git](http://try.github.io)
- [Pro Git ebook](https://git-scm.com/book/en/v2)
- [Learn Enough Git To Be Dangerous](https://www.learnenough.com/git-tutorial)
