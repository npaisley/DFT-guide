# A Guide to Density Functional Theory Calculations  
Written by Nathan Paisley  
2022  

 
---
## The Purpose of This Guide
This guide is intended to help teach you how to run DFT calculations. My experience is with using DFT for optimizing structures, ensuring the lowest energy conformation has been found, and getting excited state data and that is what is covered in this guide. For background theory on DFT and computational chemistry (I would recommend the book *Introduction to Computational chemistry* by Frank Jensen) or information on running other types of calculations you will have to do further reading. There are a number of great resources online by which to learn about DFT and how to run calculations so this guide will primarily consist of a list of resources for specific topics.

## Getting Started
### Required Programs
Running DFT calculations will require you to model compounds of interest, make plain text input files, move files to and from remote servers, access remote servers from the command line, and analyze calculation data. The programs you will use to do this differ depending on the operating system you are using but I will give suggestions below (based on experience running DFT on each the three major operating systems). I have provided links for programs whih are freely available for download.  

#### Windows  

Windows may honestly be the best overall operating to run DFT calculations on. This is due to access to chem 3D (which works quite nicely for making input geometries) and WinSCP (which is quite a good program for manipulating files on remote servers). Moreover, if you activate the windows subsystem for linux (WSL) then you have access to a full linux command line which is fantastic. I fell like MobaXterm is meh but everyone else I know seems to like it.  

##### molecular modelling:  
[Avogadro](https://avogadro.cc/) (version 1.2. There is a version 2.0 but as of the time of writing it is still in teh early stages and it doesn't work all that well)  
Chemdraw / Chem3D (You should have access to chemdraw through UBC) 
GaussView<sup>a</sup>  

##### text editor:  
[Notepad++](https://notepad-plus-plus.org/)

##### sftp client:  
[WinSCP](https://winscp.net/eng/index.php)  
[MobaXterm](https://mobaxterm.mobatek.net/)  

##### comand line interface:  
[windows subsystem for linux (WSL)](https://docs.microsoft.com/en-us/windows/wsl/install-win10)  
[MobaXterm](https://mobaxterm.mobatek.net/)  

##### result analysis:  
[Avogadro](https://avogadro.cc/)  
[Notepad++](https://notepad-plus-plus.org/)  
GaussView<sup>a</sup>  

#### MacOS  

MaOS works decently for running DFT but I don't like the default terminal (iTerm is great though) and there isn't an SFTP program that I love. You can easily utilize chem3D though which is great.

##### molecular modelling:  
[Avogadro](https://avogadro.cc/) (version 1.2. There is a version 2.0 but as of the time of writing it is still in teh early stages and it doesn't work all that well)  
Chemdraw / Chem3D  

##### text editor:  
[TextMate](https://macromates.com/)  

##### sftp client:  
[Cyberduck](https://cyberduck.io/) (Its okay at best)  
[filezilla](https://filezilla-project.org/) (I have never used this but I've heard it's good)  

##### command line interface:  
[iTerm](https://iterm2.com/)  
MacOS terminal  

##### result analysis:  
[Avogadro](https://avogadro.cc/)  
[TextMate](https://macromates.com/)  

#### Linux  

Linux is awesome fo running DFT except for when it somes to making the input geometries. You can use [WINE](https://www.winehq.org/) to install chemdraw and Chem3D but it can be painful and your experience may vary. I have done this once and it worked sort of. Every other program you need will be preinstalled and every file system browser I have used also has SFTP built in (which is brilliant).

##### molecular modelling:  
Avogadro  (Version 1.2 should be available through your package manager)  
ChemDraw / Chem3D<sup>b</sup>  
GaussView<sup>a</sup>  

##### text editor, sftp client, and command line interface:  
Whatever text editor, file explorer, and terminal applications are included in the flavour of linux you are using will certainly accomplish these tasks. If the text editor that is included is not to your liking I would suggest Geany as an alternative (I hear [ATOM](https://atom.io/) is quite good as well but I think it requires a better computer. This is only a problem if you're like me and install linux on POS hardware).  
##### result analysis:  
Avogadro  (Version 1.2 should be available through your package manager)  
Text editor  
GaussView*  

**NOTE:** Again, the above are only suggestions and by no means are *the* programs you have to use. Whatever you like using is whats best for you.

[a] GaussView is a payed for application made by the same company that makes Gaussian. If you are fortunate you will have access to a version you can run remotely (as long as you have enabled X11 forwarding when you connect to the server with GaussView installed).  
[b] Installed via wine  

## The Basics (aka. What the Hell is SSH, SFTP, Bash, a terminal...)   

### The Bash shell  
This is how you will communicate with the server but is also a very basic way of controlling your computer. The are many good resources online (links below) that cover how to navigate a file system all the way to writing custom scripts (aka. programs).  
[Bash Scripting Tutorial for Beginners](https://linuxconfig.org/bash-scripting-tutorial-for-beginners)  
[Introduction to Bash](https://cs.lmu.edu/~ray/notes/bash/)  

### Highly Useful Commands  
To learn more about each command or to refresh yourself on how to use it you can type `<command> --help` or `man <command>`. For more detailed explainations use google.
|command|use|
|-------|---|
|`pwd` | print the current directory|
|`cd`  | change directory|
|`ls` | list the contents of a directory| 
|`mkdir` | make directory|
|`cp` | copy |
|`mv` | move. can also be used to rename files|
|`tail` | prints the last part of a plain text file|
|`head` | prints the first part of a plain text file|
|`cat` | prints an entire text file. Be careful with large files|
|`grep` | search for a string within a file| 
|`ssh` | secure shell. How you log on to another computer system|
|`sftp` | secure file transfer protocol. Allows you to transfer files between your file systems (aka. network connected computers)|

A very useful command line tool is the pipe "|". This sends the output from one program or command (aka. what is usually printed to your screen) to the input for another. An example is searching part of a file with grep (useful when trying to get important information out of very large output files). This could be done using `tail -n 1000 Calculation.log | grep "Energy"`.  

### Wildcards
? and * can be used to replace unknown or variable strings. * is a string of any length and ? is one character. Very useful when dealing with a large amount of files that differ in small ways (ex. say you want to list all of the output files in a folder only. You could use `ls *.out` and only files matching that string, those ending with .out, will be listed).  

## Getting Started  

### Setting up a Compute Canada Account
1. Set up a Compute Canada account at this [Link](https://ccdb.computecanada.ca/security/login) following the instructions on this [page](https://www.computecanada.ca/research-portal/account-management/apply-for-an-account/).  
2. Make sure Zac approves your application
### Accessing Compute Canada Servers
Once your account is set up try logging into a compute canada server. Do this by opening a Bash terminal and typing `ssh -C <username for compute canada>@<compute canada server>` (replace the angle brackets and everything inside with your compute canada username or server name) and enter your password when prompted (if the blinking cursor doesn’t move thats fine, this is normal). For example, I would enter `ssh -C npaisley@graham.computecanada.ca` to log into the graham server.  
### Accessing The Gaussian Computational Chemistry Package
Once you have logged in try loading gaussian. Do this by typing `module load gaussian`. If it is your first time loading gaussian you will be presented with a block of text requesting you to agree to some terms. Copy this text saying you agree to the terms and email it to the email address specified (make sure to mention your compute canada user name). This will grant you access to gaussian on all compute canada servers. (additional information on the compute canada [website](https://docs.computecanada.ca/wiki/Gaussian).  
You can get access to other program packages (ex. Orca) in the same way. For example, trying to load Orca for the first time will prompt you to agree to the terms required (ex. `module load orca`).  
## Calculation Overview 
### The Basics

### Organization
I highly suggest making all files in your projects folder. After they are made move them to the scratch folder to run the calculation. Make files easy to type out and if you have a series of compounds keep the names similar as this facilitates running commands in loops (ex. a for loop to submit multiple calculations in a simple manner).  
I would also suggest having a separate folder for each project, separate folders for each compound within, and separate folders for each stage of the calculation within that (ex. optimization, RSH Opt, TD, NTOs).  

### Picking a Method
literature search is your best friend here. It is essential to match your chosen method to the type of compound you are calculating.  

## Running Your First Calculation: Geometry Optimization  

### Generating Your Input Structure
use avogadro, chem3D, gaussview, etc. If there is an option to run a molecular dynamics calculation within the program I would suggest you do that. This often gets you closer to a optimal structure and greatly speeds up the structural optimization by DFT.  

### Making Your Gaussian Input File  
Example input file below. The two blank lines at the end are quite important, if these are not included Gaussian will likely crash.  

myFirstCalculation.com  

```
%rwf=myFirstCalculation.rwf
%nosave
%chk=myFirstCalculation.chk
%mem=62GB
%nprocshared=16
# opt freq b3lyp/6-31g(d)

0 1

<xyz data>


```

### Transferring Your File
### Submitting Your Calulation
### How to Know When The Calculation is Finished
opt freq and opt=readfc freq max. If need more need higher int grid  
### Verifying Your Optimized Structure
### Running a Frequency Calculation
### Analyzing Your Results
### Why does the Freq Calculation say This is Not The Optimized Structure?
### Finding The True Ground State Structure
## TD-DFT
## TD-DFT and Charge Transfer
## Range Separated Hybrid Functionals
## Natural Transition Orbitals (NTOs)
## References and Further Reading

