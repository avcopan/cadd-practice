# cadd-practice

These are some notes for beginners on getting set up to start doing computer-aided drug design (CADD) research, based on the Volkamer Lab's excellent collection of [talktorials](https://projects.volkamerlab.org/teachopencadd/talktorials.html).

## Setting Up

### Starting from Windows

If you are starting on a Windows machine, you will need to install a separate Linux operating system called "Ubuntu" onto it.
Most of the software we will be using is designed to run on a Linux OS, because these operating systems are open-source (freely available) and are widely used in scientific computing.

Start by following [these instructions](https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/) to install the Ubuntu OS as a Windows Subsystem.

Once you have the "Ubuntu" app installed, open it.
Upon opening the newly installed Ubuntu app, you will be prompted to create a username and password. You will need this password to run any commands requiring "superuser" permissions (commands starding with "sudo").

Before moving forward, you should change one setting:
1. Click the orange Ubuntu icon in the upper left corner of your terminal window.
2. Click "Properties"
3. Check the box that says "Ctrl+Shift+C/V as Copy/Paste".

This will enable you to copy and paste in your terminal window (more on that momentarily).

Some context on what you have just installed:
Ubuntu is the most popular instance of the broader family Linux operating systems.
The Ubuntu "app" that you are installing is sort of like a separate computer within your computer.
You will interact with this Linux "subsystem" through a [terminal](https://en.wikipedia.org/wiki/Computer_terminal) window, which is just a window that allows you to enter operating system commands.
In a moment, we will show some simple commands to do things like print to the screen, move from one folder (or "directory") to another, tell you which directory you are in, list contents of a given directory, download a file from the internet, etc.

Different terminals have different languages that are used to enter terminal commands. This one uses the [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) command language.
As a first attempt, let's use the `echo` command to print a message to our screen:
```
echo "HELLO WORLD"
```
You should see that it prints `HELLO WORLD` to your screen.

Your Ubuntu OS has its own file system. To figure out where you are in your file system, use the "print working directory" command:
```
pwd
```
If you ever need to, you can access your Windows file system as a "mounted drive" by navigating to `/mnt/c/Users/<your username>`.
You can do so with the "change directory" command.
```
cd /mnt/c/Users/<your username>
```
If you aren't sure what your user name is, you can start typing and press tab to see the available options along the way.

To see what's in the directory you navigated to, you can use the "list" command:
```
ls
```
If you need to, you can learn more terminal commands from [this tutorial](https://linuxjourney.com/lesson/the-shell).

I will give you all of the commands you need here to install the necessary software, so you can wait to learn more unless you are interested.
