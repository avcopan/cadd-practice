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
Ubuntu is the most popular flavor from the broader family of [Linux](https://en.wikipedia.org/wiki/Linux) operating systems.
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


### Installing Conda

[Conda](https://en.wikipedia.org/wiki/Conda_(package_manager)) is a powerful package-manager for scientific computing.
You can think of it like an "app store".

If you are on a Linux machine or using a Linux terminal on Windows, you can download the install script for conda to your current directory as follows using the "web get" command (to paste it in your terminal, use Ctrl+V):
```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
```
This installer script is written in the Bash language.
You can run it as follows:
```
bash Miniconda3-latest-Linux-x86_64.sh
```
You will be prompted to accept the licensing terms along with several questions. For yes/no questions, simply type 'yes'. For other questions, just hit Enter to accept the default settings. The last question will ask you you want to initialize conda. Answer `yes` here as well, even though the default is `no`. (If you miss this step and type "no", it should give you instructions at the end for running the initialization command.)

Then restart your terminal.
When you restart, you should see the word "base" in parentheses next to your terminal prompt.
This indicates that you are in Conda's "base environment".
All of your software for this project will be installed into an environment that is specific to this work.
If you do more coding in the future, you would create new environments with the necessary software.

To check that it worked, try the following command to update conda:
```
conda update conda
```
There seem to be some recent issues with allowing conda permissions on a Windows subsystem.
If you get an HTTP Error like I did, the following should fix it for you:
```
chmod -R 777 ~/miniconda3
```
after which you can try the update command again.

Once the update command is working, you should be good to go.

#### Adding Mamba to Conda

I know this is getting to be a lot, but bear with me.
Mamba is an extra package that can be installed into conda to do things that conda already does, but faster.
It's sort of like installing a fancy engine into an ordinary car -- conda is the car and mamba is the fancy engine that can make your ordinary car drive faster.
CADD requires installing lots and lots of packages that all need to work together, and so having the more powerful mamba installer to make our installations run faster is worth it.

You can install mamba with the following command:
```
conda install mamba -n base -c conda-forge
```

### Creating Your Environment

Next you will create the environment where all of your CADD packages will be installed.

I have created an "environment" file, which lists all of the packages that you want in your environment. You can download it as follows:
```
wget https://raw.githubusercontent.com/avcopan/cadd-practice/main/env.yml
```
Once downloaded, you can use mamba to install all of the packages listed in the file into a single environment using the following command:
```
mamba env create -f env.yml
```
This will create a new environment called "cadd" with all of your packages installed in it.
Even with Mamba, this may take a while to run.

> ***Note to self**: I created this environment by splicing together the [TeachOpenCADD environment file](https://raw.githubusercontent.com/volkamerlab/teachopencadd/master/devtools/test_env.yml) with the [OpenCADD environment file](https://raw.githubusercontent.com/volkamerlab/opencadd/master/devtools/conda-envs/user_env.yaml). Between the two of these, we should have everything we could ever need. Repeating packages in the list, so it's relatively easy to copy paste them into a single environment file. Note, however, that you need to leave off the pip installs and the the sphinx packages at the end can be left off as well.*

