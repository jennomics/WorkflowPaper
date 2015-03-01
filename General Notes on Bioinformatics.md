#General Notes on Bioinformatics
##Command Line/Terminal Tutorial
This workflow is written assuming that the user is using a computer running Mac OS or Linux.  It is also possible to carry out many of the computational parts of this workflow in a Windows environment but getting these steps to work in Windows is outside the scope of this project. 

Some parts of this workflow require the user to provide text instructions for software programs by using a command line interface. While potentially intimidating to computer novices, the use of command line interfaces is sometimes necessary (_e.g._, some programs do not have graphical interfaces) and is also sometimes much more efficient. To access the command line on a Mac open the Terminal program (the default location for this program is in the "Utilities" folder under "Applications").

When this application is launched a new window will appear. This is known as a "terminal" or a "terminal window." In the terminal window, you can interact with your computer without using a mouse. Many popular programs have a GUI (Graphical User Interface) but some programs used in this workflow will not. So, instead of double-clicking to make a program run, you will type a command in the terminal window. Throughout this tutorial, we will instruct you to type commands, but copying and pasting them (when possible) will reduce the occurrence of typos. We will walk you through how to run all of the programs required for this workflow, but you must first acquire a basic familiarity with how to interact with your computer through the terminal window. Below is a list of commands that will be required to use this workflow. There are many tutorials available to help you get started. 

For more information on operating in the terminal, check out
this informative video: [https://www.youtube.com/watch?v=zRZT4nQP3sE](https://www.youtube.com/watch?v=zRZT4nQP3sE)


And this interactive tutorial: [http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)


##Summary of Unix/Linux commands and terms
$ **ls**			lists files and directories (folders).  If left as just "ls" this command will list the files and directories in your current location.  If a "path" is added afterwards (e.g., ls /usr) this command will list the files and directories in that location.

$ **cd**			use to change directories

$ **cd ..**    			use to move up one directory

$ **cd directory_name** 	use to move to that directory

$ **cd ~**			use to move to the home directory of the current user	

$ **grep "some pattern" file_name** displays lines that match the pattern (contained within the quotes) for which you are searching.   If a line contains the same character multiple times it will only be displayed once.

$ **grep –c “what you want to count” file_name** 	counts the number of lines containing a specific character or sequence of characters

$ **less file_name**					view a file

A few quick definitions:

_command line_ – the command line is where you type commands in a terminal window

_script_ – a computer program. Usually computer programs are called scripts when they perform relatively simple functions that are limited in scope. Scripts are typically only run from the command line

_directory_ – a folder

_compile_ - turning a human-readable file into a computer-executable program


##Software updates
Software packages are updated with varying frequencies. Some such updates will render the instructions offered here obsolete. When this occurs, you should consult with the software manual for help. An internet search with a description of the problem you are having may prove helpful. Another option is to email the software developer; many are remarkably responsive. As a last resort, consult with a colleague who is more comfortable with bioinformatics or computer programming. It is customary to offer a small favor or gift. Most software updates will require only minor modifications. For example, we might provide you with instructions to type:

    ./software_1.2.0/software.py
but a more recent release might necessitate:

    ./software_1.3.0/software.py