#Organism identification using 16S rRNA gene sequence
It is necessary to screen the 16S rDNA Sanger sequencing results for possible genome sequencing candidates. We recommend starting with BLAST results, then continuing onto the Genomes Online Database (GOLD).  This is a large database containing most sequenced genomes and many ongoing sequencing projects.  Sometimes the use of GOLD and an internet search will be sufficient to obtain information about the organism you have isolated. In many cases, it will be useful to build a phylogenetic tree to aid in identification, as the BLAST search results may not be sufficiently informative.

##BLAST 16S rDNA sequence
Begin by navigating to the Standard Nucleotide [BLAST at NCBI](http://blast.ncbi.nlm.nih.gov/Blast.cgi?PROGRAM=blastn&PAGE_TYPE=BlastSearch&LINK_LOC=blasthome)

Paste in your Sanger consensus sequence. We recommend checking the box to exclude Uncultured/environmental sample sequences, since these will not be informative for identification. Be sure the nucleotide collection (nr/nt) is selected under database and click the BLAST button.

##Interpreting the results
Depending on the quality of the Sanger sequencing and the particular bacteria sequenced, the BLAST search results can range from definitive to relatively uninformative. Examples of both are discussed below.

1. In some cases it is not necessary to build a phylogenetic tree for further identification. If all of the top hits are the same species (or end in sp.), have _e_-values of 0.0, good query coverage, and 99% to 100% identity, you can proceed to "Using GOLD".
2. In other cases, the results are more ambiguous. The results may show more than 99% identity to multiple species within multiple genera. In this case, proceed to section 11 "Building a 16S rDNA Phylogenetic Tree", before using GOLD.
3. Another possibility is that you will get significantly less than 99% identity to any sequences in the NCBI database. One explanation for this is that your sequence is of poor quality. This might require more stringent trimming using SeqTrace or even resequencing if the quality is poor enough to make assigning taxonomy difficult. Another possibility is that you have isolated something that is not very closely related to anything in the NCBI database. In the latter case, we would recommend first re-doing the BLAST search, but unchecking the "Uncultured/environmental sample" to see if the sequence matches others that have been found, but are not associated with a cultured organism. In either case, we would recommend re-sequencing for confirmation and then proceeding to section 11 "Building a 16S rDNA Phylogenetic Tree" to examine the phylogenetic context of the novel sequence.

##Using GOLD (the Genomes Online Database)
Go to: http://genomesonline.org/cgi-bin/GOLD/index.cgi

Under the Search tab, click the "Quick Search" option and you should be taken to a page that looks like the screen shot displayed in Figure \ref{fig:GOLD}.

Fill out the blue Organism Information (Organism Name) section, with information about your microbe from BLAST and click submit search. We usually search for only the genus to get a sense for how well that genus is represented in the database and which species are present. Figure \ref{fig:GOLD\_results} shows an example screen shot of the results for "_Brachybacterium_." Clicking on a project ID will take you to a more detailed description of the project including its project status (complete, permanent draft, incomplete, targeted).  While some "incomplete" and "targeted" projects will be completed, many will not, so we tend to ignore these categories.

If you have relatively ambiguous identification results (_e.g_. you think you have some sort of _Brachybacterium_ but aren't sure which species,) it could be worthwhile to perform an alignment of your 16S sequence with those from genomes already in Genbank or to built a phylogenetic tree as in Section 11.

##Align 16S Sequences using Align Sequences Nucleotide BLAST
First locate the 16S sequences of the genome you'd like to compare to, by searching the NCBI Nucleotide database for "Species 16s gene".

http://www.ncbi.nlm.nih.gov/nuccore/

Click on the sequence of interest, then click on the "FASTA" link to get the sequence in FASTA format. Now navigate to the ["Align Sequences Nucleotide BLAST" page](http://blast.ncbi.nlm.nih.gov/Blast.cgi?PAGE_TYPE=BlastSearch&BLAST_SPEC=blast2seq&LINK_LOC=align2seq)

Paste in the two 16S rDNA sequences and click on the "BLAST" button. Unless both your sequence and the sequence to which you are comparing were amplified with the same primers, the query coverage will not be 100%. A low identity can be the result of poor sequence quality or taxonomic distance. 

A choice of whether to sequence an organism based on these results depends on the project goal. For example, an identity of 100% suggests that at least at the 16S level, the candidate organism is very similar to what is already in the database. However, many organisms vary greatly in gene content between strains and an additional genome may still be informative. The use of 16S rRNA gene sequence percent identity as a proxy for species delimitation in bacteria is a subject of some debate in the field. \cite{Chan_2012}\cite{Drancourt_2005}\cite{Hanage_2006}\cite{Stackebrandt_2002}.

