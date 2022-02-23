# A Guide to Density Functional Theory Calculations  
Written by Nathan Paisley  
March, 2021  

 
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

Line endings, ssh, sftp, bash, terminal, server, resources, bash crash course/a handful of useful commands

## Getting Started  


### Setting up a Compute Canada Account
### Accessing Compute Canada Servers
### Accessing The Gaussian Computational Chemistry Package
## Calculation Overview 
### The Basics
aka. why do we run DFT this way. why not on our computers. how does the server work.
### Organization
### Picking a Method
### Best Practices
## Running Your First Calculation: Geometry Optimization
I am going to use your first calcultion to go over how the entire workflow works and good practice
### Generating Your Input Structure
### Making Your Gaussian Input File  

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

