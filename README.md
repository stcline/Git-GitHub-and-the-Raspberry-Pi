### In this activity, you will learn how to track changes to code projects on your Raspberry Pi using Git, a popular version control system used by professional developers.

## 0. What is Git? [Source](https://projects.raspberrypi.org/en/projects/getting-started-with-git/2)

Git is a version control system (VCS) for tracking changes to files and coordinating changes between multiple people who are all working on the same code base.

One way to think about Git is to imagine a magical school bag. You can pull books out of your bag and do some work whenever you like. Once you’ve finished your homework, you can put the books back into your school bag, and the bag remembers what changes you made to all the books inside it.

What’s really clever is that this school bag can be synchronised with another magical school bag that lives in the clouds. Whenever you like, you can tell the bag to copy the contents of all the books to the sky-bag. If you lose your own school bag, you don’t have to worry, as you can just get a new one and grab all the books and writing from the sky-bag.

That’s not all though. All your friends at school also have magical school bags. They also keep their bags synchronised with the sky-bag. This means that you and your friends can all work on the homework together. If a friend has a better answer to a science question than you do, you can copy their answer from the sky-bag to your book.

It gets even better than that: your teacher also has a magical school bag. When she wants to check the homework, she just copies all the books from the sky-bag to her bag. She can then check through the answers from the whole class in one go. If she spots a mistake, she can write a comment in the margin of the book, and then all the magical bags from the whole class will receive the comment. Only one person in the class needs to correct the mistake though, and then everyone in the class immediately has the correct answer.

## 1. Introduction

- Git is a tool that tracks changes to files and lets multiple people work on the same project safely. 
- We will use the Raspberry Pi terminal for all commands.  To do this we will use a technique called Secure Shell or SSH.

## 2. Check and install Git on Raspberry Pi (This step may be skipped if Git is already installed).

Include a short section with commands:

```bash
sudo apt update
sudo apt install git
git --version
```

## 3. Configure Git on the Pi (This assumes that you already have a GitHub Account)

Show how to set user name and email globally:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global core.editor nano
```

You’re going to be working in a terminal window for the duration of this resource, so open it up by clicking on the icon on the desktop, or by pressing `Ctrl + Alt + T` on your keyboard.

## 4. Create a project folder and initialize a repository

In the terminal, you can use the mkdir (make directory) command to create a new directory.

```bash
mkdir sensor-logger
```

Now you want to go into that directory. You can use the cd (change directory) command to do this.

```bash
cd sensor-logger
```

Next, you can create a file that will tell people what the project is about. You can use any text editor to do this, such as Notepad, TextEdit or Gedit. Create a file called `README.md`. The `.md` extension stands for **Markdown**, which is a markup language. You can learn more about Markdown [here](https://daringfireball.net/projects/markdown/).

In order to make the markdown file, you will open the **nano** text editor.  This is a simple text editor that is frequently used in Linux.  

```bash
nano README.md
```

Describe your project here.  Say something like this.

```bash
# Sensor Logger
 This is a project that uses multiple long-range ultrasonic sensors to find and track
 an object flying in three-dimensional space. It displays the object's coordinates,
 speed, and trajectory through a VR headset.
```

Pressing `Ctrl + X` will cause a save prompt to appear. You can type `Y` to save and then hit `Enter` to close nano.

Your file should have been created and will now be sitting in your directory. You can type `ls` in the terminal to see a list of files.

At the moment, the directory is just like any other directory on your system. You now need to make the magical school bag part. This is known as a **Git repository**, and it takes the form of a hidden directory that keeps track of all the changes to the working directory. Type the following to create the repository, which from now on will just be called a **repo**:

```bash
git init
```

If you type ls again, nothing will appear to have changed. You can use `ls -a` to see all the hidden files and directories, though.

You should now see something like this in your terminal window:

```  .  ..  .git  README.md```

That `.git` directory is the **repo skeleton**. You can have a look inside it by typing the following.

```bash
 ls -a .git
```

This should bring up something like this:

``` branches  config  description  HEAD  hooks  info  objects  refs```

You don’t really need to worry about this directory at all now. Just know that it is there and that it is tracking all the changes to the parent directory `sensor-logger`

### Review:
- `mkdir` creates a directory.
- `cd` moves into it.
- `ls` lists all non-hidded content in a directory.
- `ls -a` lists all content in a directory.
- `git init` turns the folder into a Git repository.
- A `README.md` file is a **Markdown** file traditionally used in a repo to describe the content of the project.

## 5. Create a simple file and make the first commit

Now you have a repo but we have not added anything to it yet, even though it looks like we have.  That `README.md` file has not been put in the repo yet.  Imagine that you have a bag which is the repo.  We need to tell Git to put things we make in it.  Let's add the  `README.md` file to our repo.

```bash
git add README.md
```

Sometime it’s easier to just add everything to the repo though, rather than adding individual files. To do this you can type:

```bash
git add --all
```

Now Git knows it needs to keep track of all the changes that happen to the `README.md` file. You can have a look at the status of your repo at any time by typing the following:

```bash
git status
```

You should see something like this:

```
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md
```

The above response is telling you that the `README.md` file has not yet been **committed**. This means that although Git knows about the file, it doesn’t yet have any of the file’s contents stored. The simplest way to do a commit is by typing:

```bash
git commit -am "add README.md"
```

This commits all changes you have made in the directory to the Git repo, and adds a message saying what you did. The message can be anything really, but it’s best to keep it fairly short yet descriptive of what you changed.

Now run `git status` again and compare the results to above.

### Review:
- `git add` moves a file into the repo and prepares it to be **committed** to the repo.
- `git commit` makes the change to the repo from the list of files to be added (or deleted).
- `git status` check the repo to see where we are on the project.


## 6. Edit files and create more commits

Now that you have set up your repo, it’s time to get on with the project. Using what you learned above, open the **nano** editor and create a file called `accelerometer.py` and enter some lines of Python code (They don't need to do anything, just make something up.)  Next, create another file with **nano** called detection-rules.json and put a welcome message in it.  After you are done with both of these actions do the following:

- Add all files to your repo.
- Commit them with a commit message in future tense.
- Check the status of your project to confirm that there is "nothing to commit".

Take about ten minutes now and make changes to your Python file.  This file can do whatever you want it to but what we are trying to do here is just make a bunch of changes.  Every time you make a change, `add` the change and `commit` the changes to your repo.

Now imagine that you’ve made a horrible mistake. You’ve been working for a while and you’ve deleted your `sense_distance()` function, and then performed a commit. With Git, it’s easy to go back in time and restore an earlier version of any of your files. Let’s first look at the commit history of the file.

```bash
git log accelerometer.py
```

This will produce something like this:

```
commit f72a9b5d635da131f3bee48a73999512869b1744 (HEAD -> master)
Author: stcline <stcline@comcast.net>
Date:   Thu May 7 11:38:15 2026 -0700

    delete function

commit 0c5443400dd961428e86faf8923c507a75f0947f
Author: stcline <stcline@comcast.net>
Date:   Thu May 7 11:37:17 2026 -0700

    add function

commit f7607fe4560b9b2e2e23037b5d118fc4803dfd8a
Author: stcline <stcline@comcast.net>
Date:   Thu May 7 11:34:42 2026 -0700

    modify accelerometer.py

commit b81ee3cdc0e9f103f9132e5092c132e192c74b96
Author: stcline <stcline@comcast.net>
Date:   Thu May 7 11:33:21 2026 -0700

    add accelerometer.py
```

You can see that in that last commit (the one at the top) was where the function was deleted. Luckily the commit message has made it easy to see what was done, which is why commit messages are important. However, typing `git log -p accelerometer.py` would have actually shown the changed contents of the file, if the commit message wasn’t clear enough.

You can now get back the version of the file from the commit before. The long string of characters after the word ‘commit’ is called a hash, and is used by Git to keep track of files. In this case, the commit that needs to be restored is 0c5443400dd961428e86faf8923c507a75f0947f. So typing the following will get the file back to the way it was:

```git checkout 0c5443400dd961428e86faf8923c507a75f0947f accelerometer.py```

The file will be restored and you can now commit this change.

```bash
git commit -am 'restore distance function'
```

## 7. Connect to a remote (e.g., GitHub)

It can be veru useful to be able to save your repos on a cloud remote like GitHub.  This allows you to work with others and on multiple devices.

1. Create a new repo on GitHub via the browser
   
3. Then on the Pi:

```bash
git remote add origin https://github.com/your-username/your-repo.git
git branch -M main
git push -u origin main
```

Describe that:
- `git remote add origin` links the local repo to the GitHub one.
- `git push` uploads commits. [sites.google](https://sites.google.com/site/cartwrightraspberrypiprojects/home/ramblings/tutorials/using-github)

## 8. Practice section

At the end of your markdown tutorial, add a short practice checklist, for example:
- Add a new file, stage it, and commit it.
- Make a small change, inspect `git status` and `git diff`, then commit.
- Run `git log` and interpret the history.

***

To move forward usefully: what’s the next thing you’d like help with—turning this outline into a teacher-facing markdown scaffold with headings and placeholders, or writing a student-ready version you can drop straight into a repo?
