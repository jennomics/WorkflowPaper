#Building a 16S rDNA Phylogenetic Tree

What _is_ this thing? At this point, you have an organism in pure culture, but you do not know what it is. If you found a creature crawling on the ground and
wanted to identify (or classify) it, you might look at it's morphology and ask what it most _looks_ like. If it has six legs, you might hypothesize it is some kind of
insect. If it has hard outer wings folded over its back, you might hypothesize that it is some kind of beetle. If it also had antler-style horns on its head, you might
hypothesize that it is some kind of stag beetle. If you do not have enough information available to hypothesize what kind of stag beetle you have, then you have reached the
limit of *taxonomic resolution* for your creature. 

With an unknown microbial species, the best way to identify it is to sequence one of its genes (most people
use the 16S rRNA gene) and ask what _it_ most looks like. With animal classification, commonly used key features are things like legs and wings and horns; with microbial
classification, the key features to examine are the nucleotides in different positions in a DNA sequence. Fortunately, we have computer programs to help us make
sense of the DNA sequence information. Our preferred approach to classifying microbial species is to place an unknown sequence in the context of a
phylogenetic tree of known sequences. Building a phylogenetic tree from a 16S rRNA sequence is fairly straightforward, but the interpretation of the tree can be
a bit complex. Here, we attempt to guide you through both. However, some complicated cases will require consultation with an expert in the field of
phylogenetics or systematics.

The outline of the workflow is to use the Ribosomal Database Project (RDP) to generate an alignment of the sequence with close relatives and an outgroup,
following by cleanup of the RDP headers, tree-building with FastTree and viewing/interpretation of the tree using Dendroscope.

##Obtain an RDP alignment

The goal of this section is to obtain a 16S alignment from RDP that can be used to build a tree. This procedure has the added benefit of providing an independent verification of the taxonomic assignment of your sequence based on the BLAST results.

1. Go to [http://rdp.cme.msu.edu](http://rdp.cme.msu.edu) 
2. Create an account 
3. Click on my RDP/login 
4. Upload the fasta file containing your 16S sequence 
5. Assign it a group name (this is what the program will label your sequence/organism). Choose this carefully since that will be the name on the final tree. 
6. Click the "+" next to the sequence, to add it to your cart
7. Click on CLASSIFIER at the top of the page
8. Click on "Do Classification With Selected Sequences" button. This will show you a hierarchical view of the classification of your sequence (from Phylum to Genus.) You will use this information to navigate to other sequences that you want to include in your alignment that you will use to build your phylogenetic tree. For example, Figure \ref{fig:RDP} shows the hierarchy for the _Tatumella_ 16S sequence. 
8. Click on BROWSERS. We recommend opening BROWSERS in a new tab so that you can keep the hierarchy information handy.
9. Click on "Isolates" to select only isolates for further analysis.  Then click "Browse"
10. Click on the + sign next to "Archaea outgroup." This will add an Archaeal sequence to your cart, which will be used to root your phylogenetic tree.  Even better would be to chose an outgroup within the same bacterial phyla that you know to be outside of the clade you are examining.  If in doubt, just use the Archaeal one.
11. If using the example sequence provided, click on "Proteobacteria", then Gammaproteobacteria, then "Enterobacteriales", then Enterobacteriaceae. This will take you to the Genus Tatumella, which currently has over 69 entries in it. If the genus you are working with has too many sequences to analyze easily (for example, _Bacillus_ currently has >26000,) one way to reduce this number is to exclude the uncultured taxa in the database. To do this, scroll down to the Data Set Options and click on the "Isolates" button. Click "Refresh" and you will see that there are fewer sequences in the Genus. To reduce this number further, click on the "Type" Strain button (though if you do this you'll have to build a tree later for species identification since each species will only be represented once in the tree). As a worst-case scenario, you will need to manually select a subset of organisms to include in your alignment.
12. Click on the + sign next to **genus** _Tatumella_ to add all of those sequences to your cart.
13. Click on "Sequence Cart" and confirm that your uploaded sequence, the outgroup sequence, and all of the other sequences you'd like to include in your tree are displayed.
14. Click on "download," leave the download options as the defaults (fasta, aligned, uncorrected,) and then click on the appropriate download button. Save the file and then rename it to something informative.

##Clean up the RDP taxon names

The RDP alignment will have taxon names that most of the downstream software tools will not tolerate because they consist of special text characters. So, we have written a little Perl script (cleanup.pl) that will remove those special characters and replace them with underscores. This script is included in the zip file of scripts on Figshare \cite{852a8297-50f7-4630-ae05-7645b7fb6d11}. To run cleanup.pl, first move it to your Applications folder. Then, in a Terminal window, navigate to the directory that contains the RDP alignment that you've just downloaded. Then, type:

    perl /Applications/cleanup.pl -i RDP_alignment.fa -o RDP_alignment_clean.fa

##Building the Tree with FastTree 

There are two ways to get FastTree, which will be required for building the tree from your alignment.  The first is to use Phylosift (installed in 9.1.4) which contains a working version of FastTree.  In this case, you will simply call the program from the Phylosift directory with the following command (be sure the path to Phylosift calls the correct version):

    /phylosift/osx/FastTree -nt RDP_alignment_clean.fa > tree_file.tre


The other option is to install FastTree directly, which is a bit more involved.

Go to http://www.microbesonline.org/fasttree/#Install
and download the FastTree.c program by right clicking on it and saving the link to your Applications folder. To compile the software, navigate to your Applications folder in a Terminal window:

    cd /Applications

Then, type:

    gcc -O3 -finline-functions -funroll-loops -Wall -o FastTree FastTree.c -lm

This compiling of FastTree requires a software tool called gcc (the Gnu Compiler Collection, if you want to know - see [http://gcc.gnu.org](http://gcc.gnu.org) for more detail). If your attempt to compile FastTree with the instructions above fails, the most likely reason is that you do not have gcc. You can download and install gcc from Xcode here https://developer.apple.com/downloads/index.action?q=xcode

In order to download Xcode, you will need to register as a developer with Apple which takes only a couple of minutes. After you register, click on the apple next to "Developer" at the top of the page. Then, click on the Xcode download link, which will ultimately take you to the Mac App Store, where you can follow the instructions to install Xcode. Once it is installed, open the program and open preferences (under the Xcode tab). Click on the downloads option and install the command line tools. 

Once you have successfully downloaded and installed Xcode and the command line tools, return to your Applications folder in a Terminal window and type again:

    gcc -O3 -finline-functions -funroll-loops -Wall -o FastTree FastTree.c -lm
    
Now, you should have a working version of FastTree. To build your tree, using the cleaned up RDP alignment, type the following (be sure the output name ends in ".tre" to ensure it will be recognized by Dendroscope):

    /Applications/FastTree -nt RDP_alignment_clean.fa > tree_file.tre 

##Viewing the Tree in Dendroscope
Download and install Dendroscope.
http://ab.inf.uni-tuebingen.de/software/dendroscope/

You will need to obtain a license here
http://www-ab2.informatik.uni-tuebingen.de/software/dendroscope/register/

Enter the license number into Dendrosope and then you can open your phylogenetic tree from the File menu to view it.

Once the tree is visible, the first step is to re-root the tree to the outgroup. Expand the tree by clicking the expansion button (labeled in Figure \ref{fig:Dendroscope}), then scroll through the tree to locate the outgroup. Click on the beginning of the taxa name, to select it, and reroot the tree by going to edit and selecting re-root.

We recommend viewing the tree as a phylogram which can be accomplished by clicking on the phylogram button (labeled in Figure \ref{fig:Dendroscope}). From this tree it should be possible to determine the phylogenetic placement of the candidate sequence, and in some cases to give it a name with more certainty than a simple BLAST search.  Below are examples of a relatively informative tree and a relatively uninformative tree:
 
In tree shown in Figure \ref{fig:Tree1} (genus _Brachybacterium_), our sample of interest from an assembly is "Brachybacterium muris UCD-AY4" \cite{Lo\_2013}. It falls within a clade where every named member has the same name "Brachybacterium muris", and this name does not occur elsewhere on the tree. Hence, we were confident enough to name our sample as that species. In other words, this sequence falls within a well-supported monophyletic clade of _Brachybacterium muris_.
 
In the tree shown in Figure \ref{fig:Tree2} (genus _Tatumella_) our species of interest is _Tatumella_ sp.  \cite{Bendiks_2013}. In contrast to the Brachybacterium example, here our species falls within a poorly defined clade containing multiple species. In this case we did not assign a species name to this isolate.
