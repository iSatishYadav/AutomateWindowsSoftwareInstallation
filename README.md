# Automate Windows Software and Apps' installation

## Why?
If you've installed Windows enough times, you already know the pain of installing all your Software and Apps again and again. If you haven't, let me save you the pain and show you how to:

> Automate the installation of Windows Software and Apps

## Package Manager FTW!

What we need here is something called Package Manager, which we can give some commands and it would install the software from the command line itself.

Why command line - so that we can repeat the process.

Windows doesn't have an official Package Manager, but [Chocolatey](https://chocolatey.org/) is your safest bet.

So here's what we're going to do, we need to search and list down all the software that we typically install and save that command at a place where we can refer it later. It can be on any of Drives (Google Drive, OneDrive) or if you're a developer or power user (whatever that is) - on a Git repo. I don't care, as long as you have the access to it when the time comes.

So let's get to it.

## 1. Install Chocolatey itself

From an Admin terminal (PowerShell or Windows Terminal)

````shell
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
````

## 2. Install packages
If you know alrady familiar with the package names of individual Software or the App, you can skip this otherwise you can search 

### 2.1 Search
Let's say I don't know what is the name of the Node.js package. I can serach:

#### 2.1.1 Search from CLI

````shell
choco search nodejs
````
It should return results something like that:

````shell
nodejs 16.11.0 [Approved]
nodejs.commandline 6.11.0 [Approved]
nodejs.install 16.11.0 [Approved]
nodejs-lts 14.18.0 [Approved]
...
30 packages found.

````

> Homework: What does `[Approved]` mean?

#### 2.1.1 Seach from Chocolatey site:

Visit https://community.chocolatey.org/packages to find all the supported packages. You can find all sorts of amazing Software and Apps including day-to-day Sofrware like Chrome, Zoom, iTunes - to Enterprise Developer Tools like Visual Studio, Python, Azure and AWS CLIs - and whatnot.

### 2.2 Install 

This is how you install a pacakge. From an Admin terminal:

* Node.js
````shell
choco install nodejs-lts
````

* VS Code
````shell
choco install vscode
````

Now you can save all this in a file and install, but wait "where is the automation you promised? I need my money back." Don't worry, people way smarter than me have thought about this and came up with:

## Packages.config
There's an official way to list all the packages and install from that file.

Here's what a typical package looks like:

````xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
    <package id="vscode" />
    <package id="nodejs-lts" version="14.18.0" />
</packages>
````

Save this file and in future you can install all the Software and Apps. e.g.

````shell
choco install "sample-packages.config"
````

Since I already have these pacakges installed, I got following message, but you can figure it out from here.

````shell
Installing from config file:
sample-packages.config
By installing, you accept licenses for the packages.
Installing the following packages:
vscode
nodejs-lts
vscode v1.61.0 already installed.
 Use --force to reinstall, specify a version to install, or try upgrade.
nodejs-lts v14.18.0 already installed.
 Use --force to reinstall, specify a version to install, or try upgrade.

Chocolatey installed 0/2 packages.
 See the log for details (C:\ProgramData\chocolatey\logs\chocolatey.log).
````

## Conclusion

That's it! This is how you can automate the installation of your favorite Software and Apps in a repeatable way.

If you liked this, please like and share this post. And visit https://github.com/iSatishYadav/AutomateWindowsSoftwareInstallation and give this repo a star.

Happy Hacking!

