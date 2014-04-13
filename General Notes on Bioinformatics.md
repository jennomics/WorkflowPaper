#General Notes on Bioinformatics
Command Line/Terminal Tutorial
Some parts of this workflow require use of the UNIX command line. While potentially intimidating to the first-time user, we have attempted to provide all the information required to run scripts or software in this environment.
Here are a few simple commands needed for this workflow.

A terminal window will appear. In the terminal window, you can interact with your computer without using a mouse. Many of the programs that are commonly used have a GUI (Graphical User Interface,) but many of the ones used in this workflow will not. So, instead of double-clicking to make a program run, you will type a command in the terminal window. We will walk you through how to run all of the programs required for this workflow, but you must first acquire a basic familiarity with how to interact with your computer through the terminal window. Below is a list of commands that will be required to use this workflow. There are many tutorials available to help you get started. 

More information on the terminal
For more information on operating in the terminal, check out
this video:
http://comailab.genomecenter.ucdavis.edu/index.php/Video

And this interactive tutorial:
http://www.ee.surrey.ac.uk/Teaching/Unix/



Summary of commands and terms
$ ls			lists files and directories (folders) in directory you are currently in

$ cd			use to change directories

$ cd ..    			use to move up one directory

$ cd directory_name 	use to move to that directory

$ cd ~ 			use to move to the home directory	

$ grep file_name

$ grep –c “what you want to count” file_name 	counts the number of times a file 
contains a specific character or sequence of characters

$ less file_name					view a file

command line – the command line is where you type commands in a terminal window
script – a computer program. Usually computer programs are called scripts when they perform relatively simple functions that are limited in scope. Scripts are typically only run from the command line
directory – a folder


Software updates
Software packages are updated with varying frequencies. Some software updates will render the instructions offered here obsolete. When this occurs, you should consult with the software manual for help, or an internet search with a description of the problem you are having can prove helpful. Another option is to email the software developer; many are remarkably responsive. As a last resort, consult with a colleague who is more comfortable with bioinformatics. It is customary to offer a small favor or gift. Most software updates will require only minor modifications. For example, we might provide you with instructions to type:

./software_1.2.0/software.py

but a more recent release might necessitate:

./software_1.3.0/software.py
