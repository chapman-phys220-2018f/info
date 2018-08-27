# Getting Started Guide

## Introduction

There is a lot of material covered at the beginning of this course that may seem unfamiliar, or scary. In the sage words of Douglas Adams, **Don't panic.**

<img src="https://octodex.github.com/images/femalecodertocat.png" width="25%" />

The aim of this course is to introduce you to industry-standard tools and practices, so that you will be prepared to deliver professional-grade work to colleagues. 
Much like reading and writing, computer literacy is becoming indispensible. 
Easily solved problems are largely solved already. 
The challenging problems that still remain are often too complex for traditional analytical methods to make substantial progress. 
Computational methods help augment other problem-solving methods and increase their effective scope; as a result, they have become increasingly necessary for progress. 
The rise in popularity of "Data Science" and "Big Data" is a symptom of this trend: Computational power enables novel problem solutions.

Being familiar with modern computational tools and techniques will give you an edge in the job market, and make transitioning out of college to the next chapter of your life more smooth. The material of the course may seem daunting---perhaps even overwhelming---at first, but rest assured that practice makes perfect. What is initially unfamiliar and strange will become second nature by the end of the course, and you will have gained a powerful set of new skills that can continue to evolve with the rapid pace of technology. Be patient with yourself, for polishing these new skills will only help you to be a valuable and competitive colleague in the future.

## Account Setup

Our class will be centered around three cloud-based pieces of technology: 
 1. [CoCalc](https://cocalc.org), a Linux server in the cloud with free software installed for you to use.
 1. [GitHub](https://github.com), a central hub for sharing code that has become standard in the open-source community. 
As such, you will need to make accounts in both places and make them communicate to each other.
 1. [Slack](https://scststudents.slack.com), a professional communication platform now standard in industry.

 - **Task 1:** Use your Chapman email to create a GitHub account, a CoCalc account, and a Slack account. Use your full, real name when making the accounts so that you can be easily found. The instructor should have invited you to the course GitHub Organization, the CoCalc course, and the Slack organization using your student email, so look for the invite emails.
 - **Task 2:** (Optional) If you like, you can link your CoCalc account to your GitHub to simplify logging in. In your CoCalc account, go to the Settings tab at the top of the screen (with the gear icon), and click on the GitHub logo (the *octocat* mascot logo :octocat:).
 - **Task 3:** Join the chat channel for the course in Slack. It should have the form `#phys220-YYYYs` where `YYYY` is the year and `s` is either `s` for spring or `f` for fall semester. Note that there are a variety of other Slack channels of potential interest, such as `#physics` or `#math` or `#cpsc` or `#jobopportunities` or `#gamedev` or `#chapman-robotics`, etc.
 
## CoCalc Project Setup

If all is well, you should see a course **project** in your main CoCalc window. Clicking on it will log into an *Ubuntu Linux* cloud computer that will run your class project. When your accounts and projects have all been created successfully, the instructor will add *internet access* to each one manually. Acquiring internet access in your project is necessary for connecting to external websites such as GitHub.

The browser click-interface for navigating folders, creating, and editing files is relatively self-explanatory. Questions can be handled in class, if the Help documentation within CoCalc does not already answer your question.

## Setting up the Linux Terminal (a.k.a. Bash Shell) and SSH

After you verify that your project has internet access (you can check the project Settings tab), we can connect to GitHub via **s**ecure **sh**ell keys (ssh keys). To do this, first open a Linux Terminal. CoCalc creates a new file for each running terminal instance, so it is recommended to create a primary terminal in the main directory of your project that you will use. To do this, type the word "terminal" in the search box (upper left corner of the Files tab of your project). It should report "No files found" and show a panel of possible file types you want to create with that name. Choose the button `>_ Terminal` to create a new Linux Terminal running the Bash Shell.  It should look something like this:

```
                ┌────────────────────────────────────────────┐
┌───────────────┤ Welcome to the CoCalc Terminal Environment ├─────────────────┐
│               └────────────────────────────────────────────┘                 │
│ Software: sage R ipython gap gp git latexmk isympy java julia octave python3 │
│ vim emacs nano joe gcc clang ocaml pdflatex xetex node convert mc htop tmux …│
│                                                    ┌─────────────────────────┤
│ Anaconda Python: 'anaconda3' (old) or 'anaconda5'  │ Usage: type command and │
│ Exit Anaconda:   'exit-anaconda'                   │ then hit the return key │
│                                                    └─────────────────────────┤
│ Learn about the Linux terminal:     http://ryanstutorials.net/linuxtutorial/ │
│ Experiencing any problems or is something missing?   email help@sagemath.com │
└──────────────────────────────────────────────────────────────────────────────┘
 
~$  
```

This login screen for the terminal gives a nice summary of all the useful software installed in your linux computer in the cloud, and suggests a good tutorial for how to use the bash shell.  (Be sure to also browse the many resources listed in the README of this `info` repository. For a quick introduction, see the [Linux/Bash Overview Slides](http://slides.com/profdressel/linux-bash-overview).)  Chapter 1 of your textbook covers the essentials of using the bash shell as well.

### Creating CoCalc SSH Keys

To connect to GitHub, we first need to create `ssh` keys for your linux computer inside CoCalc. You can think of these like keys to a house that allow people to access it. Instead, they are keys for your linux computer in the cloud that allow people to remotely log into it using the **s**ecure **sh**ell (or ssh) protocol.  There are two kinds of ssh key: public and private. A "public" key acts like a lock that you give to someone else, while its corresponding "private" key acts as a physical key used to unlock the lock. For example, if a computer knows your public key, then you can use your private key to access that computer. 

To create new keys for CoCalc, type the command `ssh-keygen -t rsa` into the terminal, and hit `Enter` four times. It should look similar to what is below. (Note, the *prompt* characters `~$` simply let you know that you may type a command, and that you are in your `~` directory, known as "home" and equivalent to `/home/user`.)
```
 ~$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/user/.ssh/id_rsa):
Created directory '/home/user/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/user/.ssh/id_rsa.
Your public key has been saved in /home/user/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:9f4vJzDrftWXdG8Jo60UsqEd0yDd4mq3orslN9Ju/UQ user@project-1c8479d1-dc82-4b59-be53-b8f4bfb0b917
The key's randomart image is:
+---[RSA 2048]----+
|        . .      |
|       . + .     |
|        o =      |
|         B + o ..|
|        S *E= + *|
|      .+ +.+o. o*|
|     o.=o o.o+ o.|
|      *o.o....+ .|
|     +=.. .+o..=.|
+----[SHA256]-----+
~$
```
This command has generated keys in the directory `~/.ssh/` (which is normally "hidden" from view since it starts with a `.`). 

### Adding your public SSH key to GitHub

You can now add to your newly generated "public key" to your GitHub account so that it knows who you are when you try to connect. To do this, run the command `cat ~/.ssh/id_rsa.pub` in the terminal (which con**cat**enates the contents of the file and prints it to the screen), which will produce something like the following:
```
~$ cat ~/.ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDiZS980QbZ1T+GYJky8QbKDngbH9UxPNKOencPT8rtk6PgBuk7DQrNladts32isd49LpHDgbFJhV/UqY9JvTn9xPXEaGRcgJurbbuE6YKWmKQ5Xl6rl3nLrK+zv4/VL+v4p0wRit/JFbjqSHBE
ni/TcO6dty3EaXH3o8eU/FCk+8kimoQqTnj/P8U/EHDySP0RvAC1k9LxrwKY22Az0J9kiZW7Mb6QJIZqu2mlVSpXQKcpiTEBUfOyWj9WyMiCPhtD0j/500CCAwwlQ2gNH8b3UGZpvxzlkT+wurvKknNGFKej/APpk/ehxbNzrni1oBFzCq/PVItq
gaJMG9B6HgvH user@project-1c8479d1-dc82-4b59-be53-b8f4bfb0b917
~$
```
The string beginning with `ssh-rsa` and ending with (in this case) `917` is your "public RSA key".  Highlight this string with the mouse and copy it (with the right-click menu). Go into your GitHub Account Settings (upper right corner menu on GitHub), then go to the settings tab "SSH and GPG Keys". Click on the button "New SSH Key" in the upper right, and paste your RSA key into the field labeled "Key". In the field labeled "Title", give your key a descriptive name so you know which key it is, for example, "CoCalc PHYS220 Key". Then click the confirmation button "Add SSH Key".

To confirm that your public key is installed correctly, go back to your Bash Terminal in CoCalc, and type the command `ssh git@github.com`. This tries to log into GitHub using your private key via secure shell (ssh), assuming the account name `git` at the address `github.com`. You should see something like the following:
```
~$ ssh git@github.com
PTY allocation request failed on channel 0
Hi YOUR_GITHUB_USERNAME_HERE! You've successfully authenticated, but GitHub does not provide shell access.
Connection to github.com closed.
~$
```
The important statement to find here is `You've successfully authenticated`. This means that GitHub understands your key properly, and you can communicate between your CoCalc linux computer and the GitHub server via `ssh`.  If you refresh your "SSH and GPG Keys" settings page in GitHub, you will now see your key has a green light next to it to indicate that the connection has been successfully confirmed.

## Cloning the Information Repository

As a check for the connection to GitHub and a demonstration that it works, using the Linux Terminal let's **m**a**k**e a new **dir**ectory to store `git` repositories using `mkdir`.
```
 ~$ mkdir ~/PHYS220/
 ~$
```
Now **c**hange into that **d**irectory using `cd` and **l**i**s**t its contents with `ls`.
```
 ~$ cd PHYS220
 ~/PHYS220$ ls
 ~/PHYS220$
```
Since the directory is initially empty, nothing interesting should be listed, so the prompt returns immediately.

Go to your GitHub account in a different tab/window and find the information repository main page. In the upper right corner, you should see a green "Clone or Download" button. Click the button and it will open up a sub-panel with a clone link. There are two possible links, HTTPS or SSH. Make sure you choose SSH. Click on the copy button to copy the repository clone link to your clipboard.

Return to your terminal and use `git clone` to clone the information repository to your directory "PHYS220". It should look something like:
```
 ~/PHYS220$ git clone git@github.com:chapman-phys220-2018f/info.git
Cloning into 'info'...
remote: Counting objects: 20, done.
remote: Compressing objects: 100% (19/19), done.
remote: Total 20 (delta 6), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (20/20), 131.57 KiB | 0 bytes/s, done.
Resolving deltas: 100% (6/6), done.
Checking connectivity... done.
~/PHYS220$ ls
info
~/PHYS220$
``` 
Now the list command `ls` shows that there is a new directory `info` that has been cloned from GitHub. You can confirm that it exists outside the terminal by going to the Files tab in your project and browsing around. The cloned files are now local inside your cloud computer, and can be viewed directly.

The above procedure will be how you clone all classwork and homework repositories for the class. For more information about how GitHub works, see the [Git and GitHub Overview Slides](http://slides.com/profdressel/git-overview). Chapters 15 and 16 of your textbook also give a detailed overview of how to use both `git` and GitHub productively.

## (Optional) Connecting Your Laptop to CoCalc

It is completely sufficient to use your browser to interact with your CoCalc computer. However, it is also possible to connect to the CoCalc computer via `ssh` from your laptop, which can help eliminate latency in the terminal. The procedure for doing this is very similar to the procedure above for connecting CoCalc to GitHub: you first create `ssh` keys on your own laptop, then tell your CoCalc account what the keys are.

If you use Linux or Mac, you can simply open a terminal and follow the above procedure for creating new `ssh` keys for your laptop using the command `ssh-keygen -t rsa`. (On a Mac, go to the Applications folder, then Utilities to find the Terminal application.)  If you use Windows, then you must first install the [Git for Windows](https://git-scm.com/download/win) application, and use the program "Git Bash" as your terminal. (When installing Git for Windows, be sure to select the option to only use git from within bash. The other default options are fine.)

Once you have generated keys on your laptop, print the public key `~/.ssh/id_rsa.pub` to the screen and copy it. Then go to CoCalc and look in the upper right corner to find your Account tab. In the Account area look for the "SSH Keys" tab and click on it. You can now paste your public SSH key into the Key field on the right, give it a descriptive title (like "Laptop RSA Key"), and click "Add SSH Key". The key should show up in the list on the left. 

To find the connection information for your project, go to the tab for your project and click on the Settings button directly under the tab. In the lower left of the settings you will find a section called "SSH Keys" that has a field prefaced by "Use the following username@host:". The long string of numbers ending with `@ssh.cocalc.com` below that is your CoCalc username for your particular project computer. You can then check whether you can connect from your laptop to CoCalc by opening a terminal on your laptop and typing `ssh USERNAME@ssh.cocalc.com` where the proper `USERNAME` for the project should be copy-pasted from CoCalc. If all is well, you will have a bash terminal connected to your CoCalc computer and can use it in exactly the same way as in the browser terminal interface.

