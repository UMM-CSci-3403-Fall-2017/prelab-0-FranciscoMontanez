# Command Line Introduction pre-lab preparation

This is the pre-lab preparation for the [Command-line-introduction lab](https://github.com/UMM-CSci-Systems/Command-line-introduction). This lab and pre-lab cover:

* The basics of using the command line and the `bash` shell
* Using a command line editor
* Writing simple `bash` scripts
* Using `git` and Github as tools for managing changes to code

One of the consistent messages we get from alums and employers is that people really need to know how to interact effectively with the command line. It's nice to use nifty GUI tools when they're available, but there are times when the only access you have to a box is via the command line. You might have to `ssh` to a server in the cloud, for example, edit a configuration file with a command line editor, commit and push those changes, and then restart a service. It might be that none of those steps is very hard, but if the command line freaks you out it can be a nightmare. Also both `emacs` and `vim` cope fairly gracefully with editing very large files, where many GUI editors don't; we have editing multi-gigabyte text files with both `emacs` and `vim`.

So one of the key goals of this lab is to begin to gain familiarity with the command line and command line editors. One lab won't make you an expert, but hopefully it will be a useful step in helping you feel more competent.

**Table of Contents**

  - [Key tasks](#key-tasks)
  - [Picking a command line editor and starting to learn it](#picking-a-command-line-editor-and-starting-to-learn-it)
  - [The basics of `bash` and Unix command line tools](#the-basics-of-bash-and-unix-command-line-tools)
  - [Forking and cloning a project using `git` and Github](#forking-and-cloning-a-project-using-git-and-github)
  - [Demo screencast series on `git`, Github, and shell scripting with `bash`](#demo-screencasts)
  - [What to do](#what-to-do)

## Key tasks

* Command line tools
    - [ ] Pick a command-line editor and start to learn it
    - [ ] Start reading about 'bash'
* `git`/Github
    - [ ] Start reading about 'git' and Github
* Demo videos
    - [ ] Watch the demo screencasts on `git`, Github, and shell scripting with `bash`

---

## Command line tools

### Picking a command line editor and starting to learn it

It's enormously useful to know how to use a command line editor for those times when you don't have access to all the nifty windowing stuff that we've grown so happily used to using. Your best options are probably `emacs` and `vim` (or its less sophisticated ancestor `vi` ).  There are many other options, but these two are some of the more popular *powerful* options (I'll outline a few reasons below)

Some people prefer more user-friendly options like `nano` or `pico`, but if you are starting from scratch it is not a bad idea to pick one with a tougher learning curve like `vim` or `emacs`.  They are harder to learn at first, but offer much more powerful options later. Both `emacs` and `vim`, for example, provide powerful macro facilities that let you "record" and "play back" a sequence of keystrokes so you can quickly repeat a complex modification (something you couldn't do with search and replace) numerous times in a large file.

Both Nic and Peter know both `emacs` and `vim`; Nic is likely to (still) use `emacs` these days, while Peter typically uses `vim` now. There are long and drawn out religious wars between fans of the two editors which we will not enter into. We will point out a few differences, however:

* Almost every version of linux or unix comes with `vi` "out of the box". Because of this, `vim` is set to be the default editor in a lot of systems. This alone is reason to know at least the bare basics of `vim` since you're almost guaranteed to find yourself in it at some point, and it would be nice if you could at least save and exit without hurting yourself.
* Emacs is big, which is why it isn't a default part of many small Linux installs. It has a Turing complete scripting language and in many ways was designed to provide an entire "windowing" user environment before we had "real" GUI windowing environments. This obviously cuts both ways – you can use the `elisp` scripting language to do crazy complex customizations and extensions, but we don't know anyone who knows and uses more than a fraction of `emacs`' power.
* `vim` is _modal_ and `emacs` isn't. In `vim` you have different modes; in "normal" mode you can navigate manipulate text, for example, where you need to switch to "insert" mode to just type text. Different people respond to in very different ways to this kind of modality; lots of people (including Peter) don't mind it at all, where it drives Nic crazy.
* `vim` tries to improve efficiency by having the most commonly used navigation keys on the "home row" (the position at which a touch-typist's hands rest).  The arrow-keys still work as expected in `vim` (not necessarily in `vi` however).  Again, some people love this, and some people hate it.

The Internet is awash in materials on both editors:

* The tutorial http://vim-adventures.com/ was fun (although it is **now** pay-to-play if you want to save your progress)
* A Wikibook: ["Learning the vi Editor"](https://en.wikibooks.org/wiki/Learning_the_vi_Editor)
* [A tour of Emacs](http://www.gnu.org/software/emacs/tour/)
* [The _Mastering Emacs_ reading guide](https://www.masteringemacs.org/reading-guide)
* [Absolute beginner's guide to emacs](http://www.jesshamrick.com/2012/09/10/absolute-beginners-guide-to-emacs/)
* [Cult of vi vs church of emacs](https://en.wikipedia.org/wiki/Editor_war)

### The basics of `bash` and Unix command-line tools

Unix and Unix-like systems provide an incredibly powerful collection of command line tools for processing and manipulating files and their contents. Over the course of these labs we'll cover what may seem like a _ton_ of command line material, but which will in fact only be a fraction of what's possible.

Many of you will come into this with almost no experience with the Unix command line, while others may already have a fair amount of practice with these tools. Luckily there are a _lot_ of good resources on the Internet to help get us all up to speed. A few tutorials that we think should be helpful:

* ["Learn Enough Command Line to Be Dangerous"](https://www.learnenough.com/command-line-tutorial)
* ["Linux tutorial" by Ryan Chadwick](http://ryanstutorials.net/linuxtutorial/)
* ["BASH Programming - Introduction HOW-TO"](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

These are in roughly decreasing order of "chattiness". The "Learn Enough" tutorial is complete with sidebars and XKCD (relevant) comics, where the "BASH Programming" introduction is from 2000 and much more terse and "business-like"; the Chadwick tutorial is somewhere in between. They also don't cover exactly the same material in the same order; if you find one's coverage of a concept (e.g., pipes) doesn't make a lot of sense, have a look at how it's covered in one of the other tutorials.

Alternatively, if you prefer videos/screencasts, these two series:

* [Linux commands for beginners](https://www.youtube.com/playlist?list=PLT98CRl2KxKHaKA9-4_I38sLzK134p4GJ)
* [Introduction to `bash` scripting](https://www.youtube.com/playlist?list=PLT98CRl2KxKG2RCPkG6EPOA-g1FmLfcZl)

cover essentially the same material, but again in a quite different order and with a different style. (You'll notice that the narrator is using `nano` as their editor – _you_ should be using the editor you choose earlier.) These videos do a pretty good job about starting from the bare minimum, but:

* It's hard to go back and find previous information
* Following along with the video can be a lot slower than following along with text for some people

In order to prepare yourself for this lab, and others that will follow, you should go through one or more of these (or something similar you find on-line that's more to your taste). We don't really care _which_ one you do, but we will expect you to have gone through something like this and made some effort to explore and practice with soem of the basic tools. This is likely to take a few hours (especially if you "play along" at home, which you'll really want to do if you want to _learn_ these concepts and tools), so don't assume you can just bang through one of these in 15 minutes.

We would _strongly_ advise that you go through your tutorial(s) of choice in the lab or at least at a machine that has a terminal program with the bash shell installed so you can try some of these things out as you go along. Most Windows users won't have a version of `bash`, and if you're not sure you almost certainly don't. It's available standard out of box on Macs and Linux boxes; if you have a Mac, look in you `Applications/Utilities` and you'll find it. If you are using windows you can install `cygwin` (https://www.cygwin.com/). You can also using the MacOS `Terminal` program or something like Putty on Windows to `ssh` into a lab box and go through the tutorial that way.

As you are going through the tutorial go through it once in a quick pass and don't worry too much if things don't make perfect sense the first time. If something is not making sense on your second reading, or does not seem to be working correctly **please** ask about it.

The final thing we'll mention here is the `man` command. If during your reading or the lab you run across a command that you aren't familiar with then the `man` command can be your friend. To find out more about a certain shell function simply type

```man function_name_here```

This will bring up a page that (supposedly) describes what that function does. Navigate the man page with the arrow keys and press q to quit back to the command line. Keep in mind that man pages are written by the person or persons who created the function. This means that the man pages throughout the shell vary from extremely technical and detailed to non-existent. If the man page isn't helpful, some simple searching on-line should bring up tons of sites to supplement a confusing `man` page. :exclamation: Be careful, though, as there can be important if subtle differences between different versions of commands, and you're best off using the `man` pages on the system you're using whenever possible.

---

## Forking and cloning a project using `git` and Github

We'll use `git` through the course as a way for groups to manage shared project resources (like code) and as the primary means for you to turn in your finished work. Some of you will be familiar with `git` from previous courses, while others will have never used it before. If you've never used `git` before you might want to read https://www.atlassian.com/git/tutorials/
and https://github.com/Kunena/Kunena-Forum/wiki/Create-a-new-branch-with-git-and-manage-branches

Most of the time you will be pulling from a git hub classroom site which automagically makes a repository for you-- but for many labs you'll still need to get a copy of the repository on your local machine for editing, and upload your changes for grading.

---

## Demo screencasts

To pull all these concepts together with a pretty direct connection to the first lab, we've created [a series of screencasts](https://www.youtube.com/playlist?list=PLSAR9qWL-3y7Z--_jF7KUMUwjCwPjjJCY) that illustrate the use of `git`, Github, and shell scripting with `bash`. You should watch those before the first lab if possible. There are a total of five videos:

- [ ] Part 1 (Github forking and `git` cloning) (18:32)
- [ ] Part 2 (Testing with `bats`) (9:49)
- [ ] Part 3 (Creating a starter shell script) (21:20)
- [ ] Part 4 (Passing the tests the easy way) (13:03)
- [ ] Part 5 (Completing the solution) (31:22)

The full set runs just over 1.5 hours, and it will likely take longer if you "play along at home", stopping occassionally to try things out, rewinding to make sure you understand a step, etc. So allocate a reasonable amount of time to go through this. (Feel free to increase the speed of the videos if you don't find the rather hyper effect too off-putting.)

If you do want to play along, then you'll need to fork the demo project so you'll have your own copy to work on. You can either fork the "master" copy at Github.com (https://github.com/UMM-CSci-Systems/git-bats-demo) or (if you're a University of Minnesota, Morris, student) you can fork a copy on the U of M Github installation (https://github.umn.edu/CSci-3403-Fall-2016/git-bats-demo).

---

## What to do

By the start of next lab you should have:

   - [ ] Gone through this entire pre-lab
   - [ ] Chosen an editor and have put some time into learning how to use it
      * Emacs
      * VIM (playing vim adventures counts)
   - [ ] Gone through a command line tutorial
   - [ ] Watched the demo screencast series on `git`, Github, and shell programming in `bash`
