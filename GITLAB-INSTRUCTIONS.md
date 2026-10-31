COMP4039 / COMP3084 GitLab instructions
=======================================

# NOTE: The notes here have been adapted from COMP1005 materials developed by Jamie Twycross and others.

# Overview

Along with supporting your Docker use, this set of instructions will provide an introduction to using an appropriate **workflow** when developing your Coursework for the *COMP4039 / COMP3084 Databases, Interfaces and Software Design Principles* module. This workflow specifically involves using GitLab. We expect you to be using GitLab during your Coursework development process and to be able to demonstrate progress via pushed updates to your GitLab account. GitLab will also be the way in which you can set up and access the core files related to the Coursework.

# Introduction

[GitLab](https://about.gitlab.com/) is a web-based software platform which allows you to manage git repositories. git is a distributed version control software system that allows you to manage versions of source code. You will be using GitLab to access the core Docker configuration files and to upload new versions of your Coursework to your own private git repository on the the Computer Science GitLab server, `projects.cs.nott.ac.uk`. You will be sharing this git repository with the module convenors so that we can track progress.

These instructions demonstrate the basic **workflow** we recommend you use to work on Coursework. These instructions assume that you are using a suitable git client on a command-line interface e.g., git on Linux, git for macOS via homebrew, Git for Windows, etc.

The **workflow** of tasks is generally as follows: edit code on your local machine, commit the code (which stages it), then push your code to GitLab. You'll repeat this process again and again. What follows below is a few setup steps (Tasks 0-4) and then an example of the workflow in operation with a basic test page (Tasks 5 onwards).


# Tasks

## Task 0 - Background reading

To get an idea about what a version control system is, spend a few minutes reading the following web page. There is no need to read any more than Section 1.1 for this activity, although you should read all of Sections 1 and 2 outside of the activity, as they give a good overview of the basics of git.

* [1.1 Getting Started - About Version Control](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)


## Task 1 - Fork the project

Go to your [list of groups in GitLab](https://projects.cs.nott.ac.uk/dashboard/groups), find the `COMP4039` group, then find the `dis-docker-v2` project, select it and then click the **fork** button in the top right of the Project overview page. On the next page, select your namespace from the *Select a namespace* dropdown menu and set the visibility level to Private, then click *Fork project*.

Forking a project creates an identical copy of an existing project. You now have your own private copy of the project (in this case this activity) stored under your account on the School's git server `projects.cs.nott.ac.uk`. This fork is your Coursework repository. You will add / edit files in your forked copy as you work on the Coursework. No other student can see the changes you make to your fork.

**Note**: in your list of projects on GitLab, the master copy, which you cannot make changes to but can fork, is in this case called `dis-docker-v2`. Your forked (private) copy, which you can make changes to, is called `XXXXXX/dis-docker-v2`, where `XXXXXX` is your University user name.


## Task 2 - Add module convenors as project members on your fork

Go to your list of projects in GitLab and click on your forked project (i.e., `dis-docker-v2`). On the left side of the screen you will see a menu under the name of your project that includes the "Members" option. Select that, then use the "Invite Members" button to add the module convenors as Guest role (i.e., search for Stuart Reeves and Nazia Hameed).

The next task is get a copy of your forked project from the School's GitLab server on to your local computer so you can work on it.


## Task 3 - Clone the project

There are various ways you can do this, depending on the platform you are using. Your objective is to `clone` a copy of your fork so that you can work on it on your local machine. 

Below is an example of doing this using a command line interface, e.g., a *terminal* window in Linux or macOS, a `cmd` shell in Git for Windows, etc. Various GUI options are available (e.g., in Git for Windows), however we are only covering the command line method. 

Open a terminal whatever your flavour of operating system. To clone the project you will need its URL. You can obtain this via the project's main page and the "Code" button on the right hand side. Click this and copy the "Clone with HTTPS" address. With your git client, run the following command (or use a `clone` option in a GUI):

```bash
$ git clone https://projects.cs.nott.ac.uk/XXXXXX/dis-docker-v2.git
```

replacing `XXXXXX` with your University username. You will be asked for you University credentials (username and password). Keep your command line / shell window open as we will be using this again shortly.

The first time you run the above command it will fail. This is because the GitLab server is not expecting your University password, but rather a *personal access token*. Following the instructions in the output of the above command to generate a personal access token with read_repository and write_repository scopes, then rerun the above command and enter your personal access token instead of your University password. Make sure you keep the personal access token somewhere safe, you will need to enter it whenever you push to your repository. If you lose your token, you can always generate a new one and revoke the old one. If you want to avoid having to type your username and personal access token when using `git`, you can set up GitLab with ssh keys (instructions are in [Less typing](#less-typing)).

The code on your local machine is now an exact copy of your forked code on the School's GitLab server. Now you are going to add a file containing some code to your project.

**Note**: when you run the above command, you may get the message `git: command not found` or similar. This means you do not have `git` installed - you will need to install it. 


## Task 4 - Set up Docker

Once you have a local copy of the forked Docker configuration, you will need to initialise your it. This requires Docker Desktop - this is installed on the A32 lab machines, but if you are using your own machine you will need to download and install it. To complete this step, follow the Docker instructions in `README.md` in the `dis-docker-v2` root directory. Once you have done that, return here.


## Task 5 - Create some new code in your Docker installation

Locate your local Docker fork. This will be wherever you cloned it to in [Task 3](#task-3---clone-the-project). Create a new HTML file in your `html/coursework/` directory called `test.html`. Copy and paste the following code into that HTML file:

```html
<html>
<head>
	<title>This is a test page</title>
</head>
<body>Welcome to my test page</body>
</html>
```

Now you have created a new test HTML file, the next step is to add it to your local git repository, and then eventually push it to GitLab.


## Task 6 - Add the code to the project

In your command line shell, go to wherever your `dis-docker-v2` root directory is located (i.e., use the `cd` command in your shell), and type:

```bash
$ git add html/coursework/test.html
```

This will add the `test.html` file to your local copy of your project.

Now we better check your page loads correctly.


## Task 7 - Test your new page

In a browser, visit `http://localhost/coursework/test.html`. You should see a page with the title "This is a test page" and the words "Welcome to my test page" should appear on the page itself.


## Task 8 - Save the code to your local repository

Type the command in your terminal window:

```bash
$ git commit -am "my first commit"
```

This saves a snapshot of your code in your local repository, as well as a message ("my first commit") associated with this snapshot. What message you actually type is up to you. In general, it is good to use a message which gives a brief summary of the changes in your code you have made; these messages also communicate to others (i.e,. module convenors) who will be examining the repository about what the purpose of each commit was.

All your code is currently stored on whatever local machine you are using, so now we want to upload it back on to the School's GitLab server.


## Task 9 - Push the local code to the remote repository

Staying in the `dis-docker-v2` root directory, type the following command in the terminal and enter your University credentials when prompted:

```bash
$ git push
```

This command copies all the changes you've committed on your local computer to the School's GitLab server. Your repository on the School's GitLab server is now an exact copy of your local repository. You've therefore also backed up your work so far.


## Task 10 - Check the results on GitLab directly

Just to double check that you have indeed updated your remote GitLab repository, switch back to your web browser where you are logged in to GitLab. On your forked `dis-docker-v2` project pages, you can browse to your `html/coursework/` directory and check that `test.html` is indeed appearing. You can actually edit your files directly in GitLab, however bear in mind that these changes will not be reflected in your local repository unless you `pull` those changes back to it. We generally recommend you do not do this unless you understand how git functions. For now we are treating GitLab purely as a one-way `push`-only store for code changes.


## Task 11 - Update the code

Let's make a change to `test.html`. Edit the file and alter the body test to whatever you like:

```html
<html>
<head>
	<title>This is a test page</title>
</head>
<body>My changed body text</body>
</html>
```

We'll now update these modifications to the existing page to the School's GitLab server.


## Task 12 - Save updates in the local and remote repository

Type:

```bash
$ git commit -am "updated body text on page"
$ git push
```

As before, the first command creates a new snapshot of your code. Notice the commit message gives a brief description of the changes you have made. The second command copies your changes to the School's GitLab server.

If you are ever unsure what the status of your local repository is compared with that of the remote (i.e., the GitLab server), use the following command:

```bash
$ git status
```

This is the general **workflow** you should use during your Coursework development. Note that you do not need to add, update, commit and push changes to your code base for every single file. Often you will want to create a bunch of new code and add or update it in one single commit. What we outline above is merely a simplified version for the purposes of demonstration.



# Questions

## Less typing

Git can use two protocols, `https` and `ssh`, to communicate between your local git repository and the GitLab server. In this activity, you have been using `https`, so that every time you clone a repository or push a commit, you need to type your password. If you configure your account on the GitLab server to use `ssh` instead of `https`, then you will not need to type your password every time you push a commit. For example, [this guide](https://docs.gitlab.com/ee/user/ssh.html) shows you how to set up a ssh key for your GitLab account.

>>>
**Caveat**: due to University firewall restrictions, `ssh` access is only available when you are on the **internal** University network e.g. using a lab machine or connected via eduroam. For external access, you will need to use `https`.
>>>

# Further reading

If you have time in the activity after finishing the tasks and answering the questions, start following and exploring the links below. You should continue to explore these links outside of the activity.

* [GitLab Documentation Learn Git](https://docs.gitlab.com/ee/topics/git/) and [Gitlab Tutorial](https://docs.gitlab.com/ee/tutorials/gitlab_navigation.html) for step-by-step guides to working with git and GitLab.

* Chapters 1 and 2 of [Pro Git](https://git-scm.com/book/en/v2) give a good introduction to the basic of git.
