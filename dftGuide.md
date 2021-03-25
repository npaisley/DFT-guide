# A Guide to Density Functional Theory Calculations  
Written by Nathan Paisley  
March, 2021  

## The Purpose of This Guide
This guide is intended to teach you how to run DFT calculations. My experience is with using DFT for optimizing structures, ensuring the lowest energy conformation has been found, and getting excited state data and that is what is covered in this guide. For background theory on DFT and computational chemistry (I would recommend the book *Introduction to Computational chemistry* by Frank Jensen) or information on running other types of calculations you will have to do further reading. 

## Getting Started
### Required Programs
Running DFT calculations wil require you to model compounds of interest, make plain text input files, move files to and from remote servers, access remote servers from the command line, and analyze calculation data. The programs you will use to do this differ depending on the operating system you are using but I will give suggestions below (based on experience running DFT on each the three major operating systems).  
#### Windows
##### molecular modelling:  
Avogadro
Chemdraw / Chem3D  
GaussView*  
##### text editor:  
Notepad++
##### sftp client:  
winSCP  
MobaXTerm  
##### comand line interface:  
windows subsystem for linux  
MobaXTerm  
##### result analysis:  
Avogadro  
Notepad++  
GaussView*  
#### MacOS  
##### molecular modelling:  
Avogadro  
Chemdraw / Chem3D  
##### text editor:  
TextMate  
##### sftp client:  
Cyberduck  
##### command line interface:  
iTerm  
MacOS terminal  
##### result analysis:  
Avogadro  
TextMate  
#### Linux
##### molecular modelling:  
Avogadro  
GaussView*  
##### text editor, sftp client, and command line interface:  
Whatever text editor, file explorer, and terminal applications are included in the flavour of linux you are using will certainly accomplish these tasks. If the text editor that is included is not to your liking I would suggest Geany as an alternative.  
##### result analysis:  
Avogadro  
Text editor  
GaussView*  
*GaussView is a payed for application made by the same company that makes Gaussian. If you are fortunate you will have access to a version you can run remotely (as long as you have enabled X11 forwarding when you connect to the server with GaussView installed).  
## The Basics (aka. What the Hell is SSH, SFTP, Bash, a terminal...)   
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
### Transferring Your File
### Submitting Your Calulation
### How to Know When The Calculation is Finished
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

