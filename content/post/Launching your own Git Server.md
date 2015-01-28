+++
Categories = ["git", "server"]
Description = "Launching your own Git Server"
Tags = ["Git", "Server", "remote"]
date = "2015-01-28T11:27:59-08:00"
menu = "main"
title = "Launching your own Git Server"
draft= false
+++

In this post, I will show how to host a Git on your own server. It's like hosting your own local version of [Github](https://github.com/), that you specifically manage traffic or host the data. In fact, I'll show how to incorporate a GUI interface to this setup, called [GitLab](https://about.gitlab.com/), to make the interface simpler for non-programmer users. 


This is **GREAT** for *science research groups* who are creating computational analysis, science software, or machine code that are used in collaborations inside and outside of their lab. In fact, that's exactly why I'm using this. There is a clean, standardized version of the code that group members can clone and branch from. It's much easier to manage the project with Git. 


Also, this avoids using completely public Git servers like Github, where your code is availabe to the public. Though I'm all about open science, open source, and reproducibility, there are times (specifically in Academia, unfortunately) where hacking together privately is appropriate.


**NOTE:** This guide is taken directly from Git's documentation, but hopefully provides a simpler (and faster) set of directions for this solution to hosting your own server. 


Some of the authentication logistics is relatively hands-on for you as the admin. This leads to better security, since you are required to personally grant access to users.


## Prepping the server


*This post assumes you have sudo permissions to the server.* You are going to create a new user on this server that will host the collaborative Git repositories and allow *only* system users to perform Git actions (clone, push, pull, branch, etc.) on these repositories. System users will only be able to access this user's directory through Git. 


Let's begin:


Create the Git user

```
$ sudo adduser git
```

This will ask you for a password; it's up to you whether you want this to be password protected.


Now, we're going to want to allow access to users on the system, using some form of authentication. 


## SSH public keys


Authentication is important when allowing users to access a private server. In this example, our server is a private local server, so we use the SSH protocol (fancy word for a standard procedure) to handle this. As the admin, you'll manage user access to this server by storing authetication keys for each user. Let's create this folder:

```
$ su git
$ cd
$ mkdir .ssh && chmod 700 .ssh
$ touch .ssh/authorized_keys && chmod 600 .ssh.authorized_keys
```

Authentication is confirmed using the SSH public key, so let's make sure all users have one of these. These keys are held in the hidden `ssh` folder:

``` 
$ cd ~/.ssh
```

We're looking for two files: `id_rsa` (or `id_dsa`) and `id_rsa.pub` (or`id_dsa.pub`).


If you don't have these files, you can generate them by typing:

```
$ ssh-keygen
```

It confirms a directory path to hold the key and asks for a password (you can leave this blank if you choose).


**Every user must have a SSH public key.**


Each user needs to send you (the server admin) the contents of `id_rsa.pub`.


## Add an authorized User


Once you have their public key (contents in `id_rsa.pub`), simply append everything in that file to the `authorized_keys` file in the hidden folder `.ssh`.


## Start a project


**The admin must always manually create a bare Git repository for each project before it can be hosted there.** Simply login as the new user, and type (assuming `<project_name>` is whatever you name the project):

```
$ mkdir <project_name>.git
$ cd <project_name>.git
$ git init --bare
```

Then, an authenticated user can create that project on their own computer, add this remote server host (`<server>` in the code below) to their repo, and push changes:
    
```
$ cd <project_name>
$ git init
$ git add .
$ git commit -m 'initial commit'
$ git remote add origin git@<server>:<project_name>.git
$ git push origin master
```

while other authorized users can clone, pull and branch from the project. 