#A brief introduction to phylogeny and systematics.
In order to identify to which organism a 16S rDNA sequence belongs, as well as to provide an evolutionary context for your organism of interest, we recommend building a phylogenetic tree (see Section X). Building the phylogenetic tree is the easy part. Intelligent interpretation of the tree will require an investment of time, similar to the investment required to learn the basics of UNIX. Fortunately, there are a number of resources available for this purpose. We recommend this online tutorial (http://evolution.berkeley.edu/evolibrary/article/phylogenetics_02) or this paper by Baldauf http://research.cs.queensu.ca/home/cisc875/faint.pdf

As with UNIX, we will list some basic terms with which you should make yourself familiar before attempting to make sense of your tree.

A phylogenetic tree is a diagram representing a model of evolutionary relationships.  Phylogenetic trees have three main components: taxa, branches, and nodes. These are defined below:

* ***Taxon***. An individual or grouping of individuals.  This could be individual sequences, species, families, phyla, etc.  For phylogenetic analyses taxa are drawn at the tips of branches and thus are sometimes referred to as "leaves" on the tree. 

* ***Branch***  A representation of the evolution of a taxon over time (sometimes also known as an evolutionary lineage). There are three main types of branches in a tree.  Terminal branches are those that lead to the tips or leaves in the tree.  Internal branches connect branches to each other.  And the root branch, also known as the root of the tree, is the branch that leads from the base of the tree to the first node in the tree. 

* ***Node*** These are the points where individual branches end.  In the internal parts of a pahylogenetic tree, single branches can "split" producing multiple descendant branches.  The point are which the branches split is known as an internal node.  If a branch ends at a taxon, the end point is known as a "terminal node". 



A key part of interpreting phylogenetic trees lies in understanding the groupings of taxa in a tree.  Some terms relating to this are below:

***Clade*** A clade is a group of organism that share a common ancestor to the . Every node in the tree defines a unique clade.

***Monophyletic clade*** If every representative of a species is found in one single clade, and no representatives of that species are found outside of that clade, then that is a monophyletic clade. The concept of monophyly is important because all species should represent monophyletic groupings. If all species are not found in a monophyletic group, then taxonomic revision of that species is in order. Unfortunately for bacterial species, taxonomic revision is frequently in order.

***Rooting/Outgroup Selection*** The root is at the base of the tree, and is determined by the designation of an outgroup. The outgroup is an organism that you are confident is most distantly related to everything else in your tree. Outgroup selection is not a trivial task, but to simplify it here, we suggest always using an Archaeal 16S rDNA sequence as your outgroup.


***Bootstrap support*** This is a number, usually expressed on a scale of 0-100, but occasionally on a scale of 0-1, that provides an estimate of the confidence that a particular node defines a "true" clade, i.e., this specific group of organisms actually shares a common ancestor.
