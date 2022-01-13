# How to log into a course specific account on ieng6
Follow the instructions below!

---
## Installing VSCode

1. First I went to [https://code.visualstudio.com/](https://code.visualstudio.com/) and downloaded VSCode.
2. Then I opened and launched it.

![Image](/labReport1Images/vscodeimage.PNG) 

^^It looked like this.

---
## Remote Connecting

1. I then installed Open SSH by going [here](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse).
2. Then I found my course specific account on [UCSD Account Lookup](https://sdacs.ucsd.edu/~icc/index.php).

    Hint: Mine looked like **cs15lwi22aag@ieng6.ucsd.edu** but yours can differ

3. I went to the terminal and typed the following command!
    `$ ssh cs15lwi22aag@ieng6.ucsd.edu`

4. I then said yes to a bunch of questions, but after that you are done and connected.

![Image](/labReport1Images/remotelyconnecting.PNG) 

When it says you have successfully logged in, you're in!

---
## Trying Some Commands

There are many commands you can run in the terminal -- they are very useful! I tried many of them. 

Try the following:

* `cd` or `cd ~`
* `ls` or `ls -lat` or `ls -a` or `ls (directory)` except put your directory instead of (directory)
* `cp (directory)`
* `cat (directory)`

I tried a couple of the `cd` and `ls` commands. I also tried the `mkdir` command.
Here's what mine looked like:

![Image](/labReport1Images/tryingsomecommands.PNG) 

---
## Moving files with scp

These are the steps I took on how to move a file called `WhereAmI.java` to a remote computer.

1. First I logged off of the remote computer (you could also open a new terminal to your local computer for this step).
2. Then I created a file called `WhereAmI.java` on VSCode.
3. I typed the command `scp WhereAmI.java cs15lwi22aa6@ieng6.ucsd.edu:~/` into my terminal (replace with your own if you are following along).
4. If prompted with a password, type in your password.
5. You can also run the files stored in the remote computer on your local computer -- try the `javac` or `java` command.

Here's what I tested out:

![Image](/labReport1Images/movingfiles.PNG) 

---
## Setting up an SSH key

These are the steps I took to set up my SSH key!

1. I went to my **local computer** (a very important step).
2. Ran `$ ssh-keygen` in my terminal and followed what was prompted (Hint: You can press enter for all of it if you have nothing to add and then your key will be printed).
3. I logged into the remote computer and ran `$ mkdir .ssh`.
4. Then I logged out and ran `scp <my_directory_name> cs15lwiaa6@ieng6.ucsd.edu:~/.ssh/authorized_keys` (I replaced the my_directory_name with the name of my directory and you should too).
5. You should be done and can log into the remote computer without typing your password.

Here is what mine looked like after I logged in by followed the instructions above:

![Image](/labReport1Images/logincommand.PNG) 

---
## Optimizing Remote Running

There are some cool things you can do to optimize your running. For example, you can run commands in the same line!!

Here are some commands I choose to run (`javac` and `java`). You can pick any and run them in a row if you want.

![Image](/labReport1Images/optimization.PNG) 

---

Whew! Congratz! You made it through. These are the steps I took and I hope they help you. 

Winter Quarter 2022.
