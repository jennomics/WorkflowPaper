#Obtain the Full-Length 16S Sequence from the Assembly

    I moved this into its own little section for now, because I'm not sure exactly where it should fit in.
    
(Skip this step if you are building the tree using the 16S sequence from Sanger sequencing)

1. Go to RAST and sign in
On the “Jobs Overview" page, click on view details (under annotation progress) for the microbe you are working with.
2. Click on Browse annotated genome in SEED viewer (At the top of the page)
3. Click on Browse through the features of [organism name]
4. Under Function search for “ssurna” or “SSU rRNA”
 (if it doesn't work at first then refresh the page)
5. Find the ssuRNA that is 1400-1800 bp in length (often Illumina assemblies also have fragments of 16S sequence that are only a few hundred bp long)
6. Click on the Feature ID for that sequence
7. Click on the Sequences tab (around the middle of the page )
8. Click on Show Fasta
9. Click on Download Sequences and save as a fasta file. Rename the file to something useful.
11. Double check the identity of the sequence at BLAST:
http://blast.ncbi.nlm.nih.gov/Blast.cgi?PROGRAM=blastn&PAGE_TYPE=BlastSearch&LINK_LOC=blasthome