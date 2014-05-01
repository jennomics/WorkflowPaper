#Data Submission
This section describes how to submit contigs and scaffolds (if applicable) as a Whole Genome Shotgun (WGS) submission to Genbank. We also recommend allowing Genbank to annotate the genome themselves, since submitting RAST annotations to Genbank can be prohibitively complicated. The genomes are automatically shared with the DNA Data Bank of Japan (DDBJ) and the European Molecular Biology Laboratory (EBML). In addition, genomes from Genbank are automatically pulled into the Integrated Microbial Genomes (IMG) database hosted at the Joint Genome Institute (JGI), and are annotated there as well.  This section also describes how to submit the raw reads, in this case we use the European Nucleotide Archive (ENA) for ease of use but the reads will be automatically incorporated into the Short Read Archive (SRA) at NCBI as well.

Genbank submission requires a .sqn file containing the contigs and an .agp file describing the scaffolds (if applicable). A5 outputs a .fasta file of scaffolds which can be converted to a .fsa and a .agp file through a command line script included in the A5 program package. The .fsa file, along with a .sbt template file (created on the NCBI website) can then be converted to a .sqn file via a script available through NCBI. 

Create a BioProject at NCBI
Go to:
http://www.ncbi.nlm.nih.gov

Create an account or login with Google or NIH login

Create a BioProject at NCBI:
Go to:
https://submit.ncbi.nlm.nih.gov/subs/bioproject/
Click on New submission

Submitter-fill in your personal information (a bolded font denotes the section, while information in italics are the responses that we typically give for a genome sequencing project)
Project type
Project data type-genome sequencing 
Sample scope-monoisolate
Material-genome
Capture-whole
Methodology-sequencing
Objective-assembly
Target
	Fill out the organism/strain name 
If you have other information feel free to add it
General info
We recommend choosing “Release immediately following curation”
Project Title
	Public Description
Relevance-Environmental
Biosample-blank
Publications-blank

Once the project is submitted, refresh the page and copy down the Bioproject ID (starts with "PRJNA")

FASTA2AGP
To finish this submission you'll need the files as described below
In the terminal, navigate to the directory containing your scaffolds file

Run the fasta2agp.pl script included with A5 on the scaffold file outputted from the A5 assembly "my_scaffolds.fasta". 
Syntax is: 
    perl fasta2agp.pl my_scaffolds.fasta > my_scaffolds.agp

eg 
    perl /Users/Madison/Desktop/a5_miseq_macOS_20140113/bin/fasta2agp.pl /Users/Madison/Desktop/a5_miseq_macOS_20140113/example/phiX.a5.final.scaffolds.fasta > phiX.a5.scaffolds.agp 


If this runs successfully then you should see a both the .fsa and .agp files in your current directory.

Important Note: NCBI considers a gap of less than 10 nucleotides to be "missing information" in a contig, not a gap between contigs (whereas A5 has no minimum gap size). Therefore NCBI requires that contigs separated by less than 10 nucleotides be merged. This script performs that merging, meaning that the number of contigs in the .fsa file may be less than in your input file.  Therefore we recommend counting the contigs in the .fsa file:

To count them in the terminal use the syntax
    grep -c “>” name_of_your_.fsa_file

Important Note: If after running the fasta2agp.pl script and counting the contigs you have the same number of contigs as starting scaffolds, then you should only submit the .sqn file to Genbank and say that scaffolding did not take place (otherwise NCBI will reject the .agp file). 

Create a .sbt template
Create a .sbt template file at NCBI 
http://www.ncbi.nlm.nih.gov/WebSub/template.cgi
The BioProject # is the Bioproject ID starting with "PRJNA" which you received in a previous step, BioSample can be left blank

When you click create the template, it will automatically download to your computer as template.sbt. We recommend immediately renaming the file to the appropriate project.

Tbl2asn
Download the tbl2asn program from 
ftp://ftp.ncbi.nih.gov/toolbox/ncbi_tools/converters/by_program/tbl2asn/

If you are using Safari a window will pop up asking for login information, just choose guest and unzip the version of the program that is compatible with your operating system. Other browsers will take you to a page with a lot of tbl2asn programs, download the one compatible with your operating system.

After downloading the desired command-line program, uncompress the archive and rename the resulting file to remove the platform designation-for example, if the unzipped file is named mac.tbl2asn rename it tbl2asn

Now change the file permissions of the file (in the terminal) since transfer by FTP resets the permissions.

Syntax is:

    chmod 755 tbl2asn

Once you have changed the permissions, create a new directory and place tbl2asn along with the .sbt file and .fsa files into the folder.

Run the tbl2asn program using the following syntax. You will need to fill out the organism name, strain, location, collection date, isolation source specific to your own project. 

    path_to_program/tbl2asn -p path_to_files -t template_file_name -M n -Z discrep -j "[organism=X] [strain=X] [country=X: city, state abbreviation] [collection_date=X] [isolation-source=X] [gcode=11]"

Following the -p is the path to the directory containing the .fsa file, following the -t is the path to and name of the template file

Sample syntax
    Desktop/ncbi/tbl2asn -p ~/Desktop/ncbi -t ~/Desktop/ncbi/template-1.sbt -M n -Z discrep –j "[organism=Ruthia magnifica str. UCD-CM][strain=UCD-CM] [country=USA: Davis, CA][collection_date=2002][isolation-source=Calyptogena magnifica tissue][gcode=11]"

 

The program will output the necessary files into the directory you created earlier

(ensure no errors were generated by opening the errorsummary.val file and making sure it is blank, or listing the directory contents ($ ls –lh) to ensure it has zero bytes)

Create a Whole Genome Shotgun (WGS) Submission
Navigate to
https://submit.ncbi.nlm.nih.gov/subs/wgs/
Click on the New Submission button at the top
Submitter
-fill in your own information
General Info
	BioProject-Yes, add the BioProject identification sequence (from the BioProject submission, starts with PRJNA)
	Biosample-No
	Release date-Optional but we recommend “Release immediately following curation”
-Don’t check the box stating, “Genome assembly structured comment is in the contig .sq file”
Assembly Method-Choose other, fill in the blank with A5 Assembly Pipeline
Version or date program was run – Sample here
Assembly name – Sample here
Genome coverage- provided in the output from A5
Sequencing technology – Illumina (Miseq or HiSeq)

Is this the full representation of the genome? Yes
Is this the final version? Yes
Do you intend to annotate this version? No
Is it a part of a multiisolate project? No
Is it a de novo assembly? Yes
Is it an update of existing submission? For most projects the answer to this will be no

BioSample Type
-Select Microbe

BioSample attributes 
Sample Name
Organism 
Strain
Collection date
Geographic location
Isolation source

Files
	Select We have files for traditional split contigs OR gapped sequences 
	Select AS.1 (.sqn) and upload your .sqn file
	“Do you have AGP files that assemble the split contigs into scaffolds and/or chromosomes, OR assemble the gapped sequences into chromosomes?” If you have scaffolds that are not identical to your contigs select yes if not select no and continue onto the next section
	If you do have scaffolding
“Do you have an AGP file for unplaced scaffolds built from the split contigs (these are scaffolds without chromosome or plasmid information)?” Yes -upload the AGP file

“Are there also AGP files that assemble chromosomes, plasmids and/or unlocalized scaffolds?” No

“Did you annotate the scaffolds or chromosomes that are assembled in the AGP files (not gapped submissions)?” No

Bacteria is available from-If the bacteria is available in a culture collection, feel free to indicate where. We recommend submission of sequenced strains to a culture collection if possible.
Source DNA is available from-See above

-Check the box below to annotate this prokaryotic genome in the NCBI prokaryotic annotation pipeline before being released. This will allow NCBI to use their PGAAP pipeline to annotate the genome, and this annotation will be automatically attached to the project.

Files
Click on “We have files for contigs”
Did you assemble the contigs or other components into scaffolds and/or chromosomes? Yes
Do you have unplaced scaffolds (scaffolds without chromosome or plasmid information)? Yes-upload AGP file
Did you assemble chromosomes, plasmids and/or unlocalized scaffolds? No
Do you have sequence files for scaffolds and/or chromosomes and/or plasmids? No

Click Submit and you're done! You will receive a series of e-mails from NCBI confirming your submission and notifying you of any problems. Once the submission is pre-processed you'll get an Accession Number. Note however that the data will not be released until final processing.  The Accession Number is not acceptable for publication until after the final release of the data.

**Submitting Raw Reads to ENA/SRA**
We recommend using Safari or Firefox for this step, Chrome can have issues with the Java requirements for uploading files.

Go to:

https://www.ebi.ac.uk/ena/about/sra_submissions

And create an account

Successful creation of an account should take you to the "Welcome to ENA's Sequence Read Archive (SRA) Webin submission system." screen

Click on New Submission tab

Select Submit sequence reads and experiments

Click on Data Upload Instructions towards bottom of page	

This takes you to a variety of options for uploading files depending on your preference and operating system. We use the Webin Data Uploader. Click on the link which will download a .jlnp file. Open and run this file. Depending on your system you may have to download and install a new version of java. On some systems you may have to right-click the .jlnp file and Open with “Java Web Start”.

Login using your e-mail address and password

In the WebinDataUploader, in the blank area to the right of the Local Upload directory, navigate to the directory on your computer containing the reads (using the path as you would in the terminal) 

Select the file(s) containing the reads and click Upload. 

(Note that paired-end data is required to be in two separate fastq files, these files can be found in the A5 assembly directory as ???)

Note that the only acceptable file types for fastq files are gzip (.gz) and bzip (.bz2). To gzip files in the Terminal use the following syntax:

    gzip [filename] 

After completion, return to EMBL (the new submission tab of the SRA Webin submission system) and select the Next button.   During this process, refreshing the page or navigating away from the page will reset the form and the information will be lost.

Click Create a New Study. Fill in descriptions of the project and proceed to next tab. Select the appropriate metatdata format, or in most cases the ENL default sample checklist at the bottom.  Note that the default release date is three months from the current date, change this if the data should be released sooner.

You should now be at the Sample page. Required fields are listed on the right and optional additional fields can be selected from the options on the right. Fill out the appropriate fields and click on Next.

Note: If you are submitting data for an organism that doesn’t have a Taxon ID (“Tax ID”) then you need to e-mail ENA to receive one (datasubs@ebi.ac.uk). If you have already submitted the genome to NCBI then you can retrieve the Taxon ID from your BioProject page there. 
On the ENA page, you will be able to search for the Taxon ID and find your organism under the Organism Details tab but you won’t be able to find it using the name of the organism.

On the Sample page
Click the + Add button under sample group details 
Fill in the unique name under basic details, add the Tax ID if it wasn’t added previously and click next

On the Run page
Select the appropriate data type

Fill in the required fields (they change with data type)

Note: “Insert size” cannot be a range, only a number.


Click Submit and confirm submission. You will immediately receive a confirmation e-mail but it takes some time before the information is actually live at the ENL links.
