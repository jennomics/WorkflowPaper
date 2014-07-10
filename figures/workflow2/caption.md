\label{fig:Rocket} This figure illustrates all of the steps of the workflow. Short desescriptions of each step are listed below.

**Culture and Isolation**-Here we cover the steps necessary to take a sample through plating, dilution streaking, overnight growth, creating a glycerol stock, 16s PCR and preparation for Sanger sequencing.    
We assume a starting point of wanting to isolate an organism from a particular environment and needing to identify it.  Users starting with a known organism should proceed to "Library Preparation and Sequencing”.
Culture and Isolation covers steps 5 (Isolation) through 6.3 (PCR reaction).

**16S Sanger Sequencing**-Preparation of samples for submission to a DNA sequencing facility.

**Alignment**-Upon receiving Sanger reads from a sequencing facility, it is necessary to quality trim the reads, reverse complement the sequences, align the reads and generate a consensus sequence. This is easiest to do visually via a chromatogram allowing the user to see the trace and process the sequences manually.

**I.D. Species**-In a classroom or undergraduate research setting the researchers may not have a particular bacterial species in mind.  In this case it is necessary to screen the 16S Sanger sequencing results for possible genome project candidates.   We recommend starting with the BLAST results, then continuing onto the Genomes Online Database (GOLD), and simply Google searching.   In many cases it will be handy to first build a phylogenetic tree to aid in identification since the BLAST results may not be sufficiently informative.

**DNA Extraction**-In this step, DNA is extracted from the species of interest.

**Library Prep**-The choice of sequencing technology and of library preparation method for genome sequencing is ever-changing and much-debated.   Here we recommend using Illumina MiSeq for reasons of cost, depth of coverage, and length of reads.   Furthermore, our recommended assembly pipeline, A5-miseq, requires Illumina data and is optimized for the longer reads from the MiSeq.   
**Illumina Sequencing**-We recommend sending the samples to a DNA sequencing facility.

**Genome Assembly**-Genome assembly typically consists of data cleaning (quality filtering and adaptor removal), error correction, contig assembly, scaffolding, and verification of scaffolds/contigs.  There are a large array of programs that can perform some, or most of these steps.  These programs include commercial and open-source options, with some choice being very user friendly and some being extremely difficult to use/install.For this workflow we recommend use of the open source A5 assembly pipeline which automates all of the steps described above with a single command . 

**Verification**-There are three portions to the verification of a genome assembly.  The first is the overall "quality" of the assembly, assessed by examining the stats provided by A5 (e.g. number of contigs and contig N50).  The second is verification that the organism sequenced is the organism of interest, simply by checking the 16S sequence with BLAST.  The third is "completeness" which is difficult to measure except in cases where a close reference is available.  We use the presence or absence of single-copy marker genes as a proxy for completeness. 

**Annotation**-There are a number of different pipelines available for annotation of bacterial genomes.  These include Prokka, IMG, RAST, PGAP and others.

**Tree Building**-There are two points during the workflow where making a 16S phylogenetic tree may be useful.  The first is after identification of candidate organisms by Sanger sequencing and the second is after assembly of the genome.   The process is identical in both cases, but the additional length and improved quality of the post-assembly 16S sequence may generate a better tree.  The tree can be used for identification of the candidate (e.g. is the candidate found in a single species clade), for naming of the candidate (does it fall in a clade containing only members of that species, and other members of the species are not found outside that clade), and for placement of the organism into a phylogenetic context.
The outline of this step, is to use the Ribosomal Database Project (RDP) to generate an alignment of the sequence with close relative and an outgroup, following by cleanup of the RDP headers, tree-building with FastTree and viewing/analysis of the tree in Dendroscope.

**NCBI Submission**-This section describes how to submit contigs and scaffolds (if applicable) as a Whole Genome Shotgun (WGS) submission to Genbank.  We also recommend allowing Genbank to annotate the genome themselves, since submitting RAST annotations to Genbank can be prohibitively complicated.

**ENA Submission**-We recommend submitting the raw reads to ENA/SRA

**Publication**-This will often be a Genome Announcement in the ASM Genome Announcements Journal.
