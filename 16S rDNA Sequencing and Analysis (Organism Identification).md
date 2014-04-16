#16S rDNA Sequencing and Analysis (Organism Identification)
##16s rDNA PCR
Following the second dilution streaking, the organisms need to be identified. This is accomplished by Sanger sequencing of a 16S rDNA PCR product.

The samples can be prepared for 16S rDNA PCR via direct PCR (using the liquid culture as the template for the PCR reaction) or following DNA extraction. Direct PCR significantly decreases the amount of work needed for preparation, but it can yield poorer Sanger results, oth in terms of PCR success and resultant sequence quality. We recommend direct PCR when screening a large number of samples. DNA extraction can be used for any recalcitrant samples. DNA extraction is significantly more work, but it often generates better Sanger sequences allowing for more accurate identification.

##DNA Extraction
Depending on available equipment, experience, and cost there are a number of different options for DNA extraction. The use of Phenol-Chloroform followed by ethanol precipitation is a microbiology standard, and any number of protocols for this method can be found on the web. There are several advantages to using a commercially available kit for this purpose, notably ease and lack of harmful chemicals, but they typically are more expensive and include reagents for at least 50 samples. Our lab uses the Promega-Wizard Genomic DNA Purification Kit or the MO BIO-Power Soil DNA Isolation Kit

Follow the protocol or kit instructions provided by the manufacturer and then proceed to "PCR reaction" below.

##Direct PCR (if not extracting DNA)

Centrifuge 1mL of the overnight culture until the bacteria form a pellet at the bottom of the tube (about 5 minutes at 10,000g), pour off the supernatant and resuspend in 100ul of sterile DNAase-free water. Incubate the samples at 100°C for 10 minutes to help lyse the cells. Use the resulting solution as the template in the PCR reaction below

##PCR reaction
This reaction uses the 27F (AGAGTTTGATCMTGGCTCAG) and 1391R (GACGGGCGGTGTGTRCA) primers which amplify a near full-length bacterial 16S rRNA gene. Our lab uses either the ___ or the ___ PCR reagents, with an annealing temperature of 54 deg and an extension at 72deg of 90 seconds. Don't forget to include positive (any sample containing bacterial genomic DNA) and negative (water) controls. 

After PCR is completed, confirm the PCR reaction worked by agarose gel electrophoresis, all controls behaved as expected, and that you have DNA fragments of the correct size (380bp).  

##Submit Samples for Sequencing
Very few single-researcher labs maintain Sanger sequencing capacity. However, there are a number of DNA sequencing facilities that provide sequencing services for researchers. They will handle as few as 1 single sample, or will allow you to submit an unlimited number of samples, typically arrayed in a 96-well plate.  You will typically provide both your PCR product as well as your PCR primers for sequencing. Each facility will have its own guidelines concerning DNA and primer concentration. Our lab uses the UC DNA Sequencing Facility-UC Davis
http://dnaseq.ucdavis.edu. If a quick internet search does not reveal the presence of a Sequencing facility near you, most sequencing centers will allow you to ship samples to them for sequencing.

##Sanger Sequence Processing
Upon receiving Sanger reads from a sequencing facility, typically via email, it is necessary to do some pre-processing before they can be analyzed.  quality trim the reads, reverse complement the reverse sequence, align the reads and generate a consensus sequence. There are very limited options for free software that allow the user to perform these steps. We recommend SeqTrace for the user who wants to see the trace and process the sequences manually.

We have also created a script that will do all of these steps automatically, but does not allow you to adjust any of the parameters The choice of our script (easy, little control) versus SeqTrace (more complex, more control) will depend on the user and the project. 

##SeqTrace
Download the program from
https://code.google.com/p/seqtrace/downloads/list

Installation Directions
https://code.google.com/p/seqtrace/wiki/Installation

Installing and running SeqTrace on a PC is simple, installing it on a Mac requires a few extra steps. The installation guide offers two options for installing SeqTrace on a Mac, we recommend running SeqTrace with native GTK+

To install SeqTrace on a Mac you will need to download the PyGTK package from OSX. 
http://sourceforge.net/projects/macpkg/files/PyGTK/2.24.0/PyGTK.pkg/download

Confirm that you have Python version 2.7x or earlier. You can do this by typing

    - python --version
    
If not, seek help to invoke an earlier version directly.
http://www.python.org/download/releases/

After downloading and unpacking the program, SeqTrace is ready to go. SeqTrace must be launched from a Terminal window. For a refresher or introduction to the Terminal see section II. Move SeqTrace to your Applications folder. 

Open a Terminal window and type 

./Applications/seqtrace-0.9.0/seqtrace.py

This syntax will only work if the SeqTrace folder’s name is seqtrace-0.9.0, if you saved it under a different name you will need to replace seqtrace-0.9.0 with whatever you named your folder

This will launch SeqTrace from the terminal in a Python shell, you will need to keep the terminal window open while you are using the program. 

SeqTrace provides excellent directions for using the program at https://code.google.com/p/seqtrace/wiki/WorkingWithProjects

Edit and Create a Consensus Sequence
For this workflow we have found that the following is the simplest way to edit and create a consensus sequence from a forward and reverse read in SeqTrace.

1. Create a new project (File > New Project) 
Add your forward and reverse primer sequences here, we used 27F (AGAGTTTGATCMTGGCTCAG) 
and 1391R (GACGGGCGGTGTGTRCA) 
click ok
2. To add files go to Traces and click on Add trace files, then select the reads 
(.abi files) you want to work with. 
3. The program is able to recognize forward and reverse reads from information in the file name if they are properly formatted.

Go to Traces and click on Find and mark forward/reverse. The default setting looks for _F for forward and _R for reverse. This can be edited in the Project settings (you can pull it up by clicking on the picture of the tools at the top of the page) and changing the search strings under trace settings

