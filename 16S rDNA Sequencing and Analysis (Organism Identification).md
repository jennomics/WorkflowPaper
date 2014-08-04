#16S rDNA Sequencing and Analysis (Organism Identification)
Following the second dilution streaking, the organisms need to be identified. This is accomplished by determining and then analyzing the DNA sequence of the 16S rRNA gene. In this section we describe how the sequence of this gene is determined and readied for analysis.  The general outline is as follows: DNA extraction, polymerase chain reaction (PCR) amplification of the 16S rRNA gene, and sequencing of the resulting PCR product using a method originally developed by Fred Sanger and now known as "Sanger sequencing".  There are multiple approaches one can take to these steps.  For example, the PCR reaction needs DNA from the organisms of interest.  That DNA can come directly from a liquid culture of the organism (when this is used for PCR this is known as direct PCR).  Alternatively, one can take a liquid culture and then isolate the DNA from that culture and use the "clean" DNA as material for the PCR.  This adds an extra step to the process - a step known as "DNA extraction".  Direct PCR significantly decreases the amount of work needed for preparation, but it can yield poorer results, both in terms of PCR success and resultant sequence quality. However, we recommend direct PCR when screening a large number of samples. DNA extraction can then be used for any recalcitrant samples. DNA extraction is significantly more work, but it often generates better Sanger sequences allowing for more accurate identification.

##DNA Extraction
There are a number of different options for DNA isolation and which one should use depends on many factors including available equipment, experience, and cost. A  standard approach in microbiology involves the use of phenol and chloroform extraction followed by ethanol precipitation, and any number of protocols for this approach can be found in books, articles and on the internet.  A common alternative approach is to use a commercially available kit - there are many advantages to such kits - notably ease and lack of toxic chemicals.  A disadvantage of kits is that they typically are more expensive per sample than other approaches (especially if one is only doing a few samples since most kits include materials for at a minimum 50 samples). For most projects, we use kits - especially the Promega-Wizard Genomic DNA Purification Kit.

Follow the protocol or kit instructions provided by the manufacturer and then proceed to "PCR reaction" below.

##Direct PCR (if not extracting DNA)

Centrifuge 1 ml of the overnight culture until the cells form a pellet at the bottom of the tube (about 5 minutes at 10,000 g), pour off the liquid on top (a.k.a. the supernatant) and resuspend in 100\(\mu\)l of sterile DNAase-free water. Incubate the samples at 100 deg C for 10 minutes to help lyse the cells. Use the resulting solution as the template in the PCR reaction below.

##PCR reaction
This reaction uses the 27F (AGAGTTTGATCMTGGCTCAG) and 1391R (GACGGGCGGTGTGTRCA) primers which amplify a near full-length bacterial (and many archaeal) 16S rRNA gene. Our lab uses standard PCR reagents (Qiagen or Kappa), with an annealing temperature of 54 deg C and an extension at 72 deg C of 90 seconds. Do not forget to include positive (any sample containing bacterial genomic DNA) and negative (e.g., just water) controls. 

After PCR is completed, confirm the PCR reaction worked by agarose gel electrophoresis, all controls behaved as expected, and that you have DNA fragments of the correct size (~1350bp).  

##Submit Samples for Sequencing
Very few single-researcher labs maintain Sanger sequencing capacity. However, there are a number of DNA sequencing facilities (commercial and academic) that provide sequencing services for researchers. They will handle as little as a single sample, or will allow you to submit an unlimited number of samples, typically arrayed in 96-well plates.  You will typically provide both your PCR product as well as your PCR primers for sequencing.  Don't forget to submit forward (27F) and reverse (1391R) reactions for each sample. Each facility will have its own guidelines concerning DNA and primer concentration. Our lab uses the UC DNA Sequencing Facility-UC Davis
http://dnaseq.ucdavis.edu. If a quick internet search does not reveal the presence of a Sequencing Facility near you, most sequencing centers will allow you to ship samples to them for sequencing.

##Sanger Sequence Processing
Upon receiving Sanger reads from a sequencing facility, typically via e-mail, it is necessary to do some pre-processing before they can be analyzed.  These steps include quality trimming the reads, reverse complementing the reverse sequence, aligning the reads and generating a consensus sequence. There are very limited options for free software that allow the user to perform these steps. We recommend SeqTrace \cite{stucky2012seqtrace} for the user who wants to see the trace and process the sequences manually.

We have also created a script that will do all of these steps automatically, but does not allow you to adjust any of the parameters. The choice of our script (easy, little control) versus SeqTrace (more complex, more control) will depend on the user and the project. 

##Install and run SeqTrace
Download the program from
https://code.google.com/p/seqtrace/downloads/list

Installation Directions
https://code.google.com/p/seqtrace/wiki/Installation

Installing and running SeqTrace on a PC is simple, installing it on a Mac requires a few more steps than for a PC. The installation guide offers two options for installing SeqTrace on a Mac, we recommend running SeqTrace with native GTK+

To install SeqTrace on a Mac you will need to download the PyGTK package from OSX. 
http://sourceforge.net/projects/macpkg/files/PyGTK/2.24.0/PyGTK.pkg/download

Confirm that you have Python version 2.x. You can do this by typing:

    python --version

You should see something that looks like "Python 2.6.9" If you see Python 3.x, seek outside help to invoke an earlier version directly.

http://www.python.org/download/releases/

After downloading and unpacking the program, SeqTrace is ready to go. SeqTrace must be launched from a Terminal window. For a refresher or introduction to the Terminal see section 2. Move SeqTrace to your Applications folder. 

Open a Terminal window and type:

    ./Applications/seqtrace-0.9.0/seqtrace.py

This syntax will only work if the SeqTrace folder’s name is seqtrace-0.9.0, if you saved it under a different name you will need to replace seqtrace-0.9.0 with the name of that folder

This will launch SeqTrace from the terminal in a Python shell; you will need to keep the terminal window open while you are using the program. 

SeqTrace provides excellent directions for using the program at https://code.google.com/p/seqtrace/wiki/WorkingWithProjects

##Edit and Create a Consensus Sequence with SeqTrace
For this workflow we have found that the following is the simplest way to edit and create a consensus sequence from a forward and reverse read in SeqTrace. 

1. Create a new project (File > New Project) 
Add your forward and reverse primer sequences here, we used 27F (AGAGTTTGATCMTGGCTCAG) 
and 1391R (GACGGGCGGTGTGTRCA) 
click ok
2. To add files go to Traces and click on Add trace files, then select the reads 
(.abi files) you want to work with. 
3. The program is able to recognize forward and reverse reads from information in the file name if they are properly formatted.
 + Go to Traces and click on Find and mark forward/reverse. The default setting looks for \_F for forward and \_R for reverse. This can be edited in the Project settings (you can pull it up by clicking on the picture of the tools at the top of the page) and changing the search strings under trace settings. For an example see Figure \ref{fig:seqtrace\_1}
 + If the program is able to recognize the forward/reverse reads it will place an orange left pointing arrow in front of reverse reads and a blue right pointing arrow in front of forward reads. This step is not necessary to get a consensus sequence, it just makes organizing the reads easier. 
4. Pull up the Project Settings by clicking on the picture of tools at the top of the page. Click on the Sequence Processing tab, under Sequence trimming unclick the Automatically trim sequence ends button. You should also decrease the Min. confidence score under Consensus settings. The default option is 30, which represents a 99.9% quality score, for many reads this will be too stringent and will not allow you to get enough overlap to create a consensus sequence. A minimum confidence score between 15 and 25 is normally okay but tuning may be required depending on your read quality. For an example see Figure \ref{fig:seqtrace\_2}.
5. Group your forward and reverse reads by highlighting both of them and clicking Group selected forward/reverse files (under Traces)
6. Under Sequences go to Generate Finished Sequences and click on for all trace files. (you will need to redo this every time you change the project settings).
7. To view your consensus sequence, click on the read pair group and then click on the magnifying glass at the top of the page. You should see something like Figure \ref{fig:chromatogram}.
8. The Trace View shows the quality scores, the chromatogram display, and the raw base calls from both the forward and reverse reads, as well as the consensus sequence. The consensus sequence is the middle list of nucleotides. If the program is giving you a string of Ns where your forward and reverse reads do not overlap, you need to decrease the Min confidence score.
9. To export the consensus from the trace view, go to Sequence, hover on Export Sequences  and select Export Sequences from Selected Trace Files. This will create a file containing the consensus sequence, which can then be used for analysis such as for searching for closely related sequences using the BLAST program \cite{Altschul_1990} which can be used to identify the organism.

##Custom Script to Create a Consensus Sequence (merge\_sanger\_16s.pl)
###Download/Install
1. Create a new folder called Sanger_seq on your desktop
2. Download the zip file, containing three scripts (merge\_sanger\_16s.pl, CleanupRDP.pl and subsample\_reads.pl) from http://figshare.com/articles/Miscellaneous_Scripts_for_Workflow/1086285
3. Open the zip file and move the merge\_sanger\_16s.pl file to the new Sanger_seq folder

###MUSCLE
In order to run this script you will need to download MUSCLE \cite{Edgar_2004} from here: http://www.drive5.com/muscle/downloads.htm. Use the Archive Utility to open the file, change the name of the executable file from something like "muscle3.8.31\_i86darwin64" to "muscle," and move it into your Applications folder.

###Convert Files from .abi to . fastq

To run the merge\_sanger\_16s.pl you will first need to convert your read files from .abi to .fastq

This can be done at 
http://sequenceconversion.bugaco.com/converter/biology/sequences/

Use the drop down menus to set it to convert .abi files to .fastq. Upload a file and convert it. The converted file will save to your downloads folder under the name sample.fastq. If you are working with a lot of reads we recommend immediately renaming the files to match the original abi file name to avoid confusion.

###Edit and Create a Consensus Sequence
Once all of your files are in fastq format, move all of them to the Sanger\_seq folder in which you saved the merge\_sanger\_16s.pl script. Use the terminal to navigate to within this folder by typing:

    cd Desktop/Sanger_seq

Then, to run the script, type:

    perl merge_sanger_16s.pl file1.fastq file2.fastq
The script will return one of 2 messages:

1. "Found N conflicting case(s) during merging of X residues" 
2. "Not enough data to overlap confidently." 

In the first case the merging happened, however there may be some conflicting bases. The fewer the better. It can be an indication of how confident the user should be with the results. Since this is a very crude method it should be noted that there is no fancy algorithm behind the merge. There is a crude comparison for which we keep the base that had the highest quality score.

In the second outcome, the sequences were trimmed too much when doing the QC. The length of both sequences end to end was smaller than the fragment length that we are looking for.  This is an indication of poor quality sequence and most users should not proceed (others can lower the quality threshold set by the script).

The newly merged file will be saved as file1\_merged.fasta and can be uploaded to BLAST for identification.
