#General notes on bacterial systematics.
In order to identify to which organism a 16S rDNA sequence belongs, as well as to provide an evolutionary context for your organism of interest, we recommend building a phylogenetic tree (see Section X). Building the phylogenetic tree is the easy part. Intelligent interpretation of the tree will require an investment of time, similar to the investment required to learn the basics of UNIX. Fortunately, there are a number of resources available for this purpose. We recommend this online tutorial (http://evolution.berkeley.edu/evolibrary/article/phylogenetics_02) or this paper by Baldauf http://research.cs.queensu.ca/home/cisc875/faint.pdf

As with UNIX, we will list some basic terms with which you should make yourself familiar before attempting to make sense of your tree.

***Branch*** All of the organisms in a tree are at the tips of brances (that's why they are sometimes referred to as leaves.) All of the branches show the way in which organisms are connected (related) to each other.

***Node*** These are the points where branches connect.

***Clade*** A clade is a group of organism that share a common ancestor. Every node in the tree defines a unique clade.

***Bootstrap support*** This is a number, usually expressed on a scale of 0-100, but occasionally on a scale of 0-1, that provides an estimate of the confidence that a particular node defines a "true" clade, i.e., this specific group of organisms actually shares a common ancestor.

***Monophyletic clade*** If every representative of a species is found in one single clade, and no representatives of that species are found outside of that clade, then that is a monophyletic clade. The concept of monophyly is important because all species should represent monophyletic groupings. If all species are not found in a monophyletic group, then taxonomic revision of that species is in order. Unfortunately for bacterial species, taxonomic revision is frequently in order.

***Rooting/Outgroup Selection*** The root is at the base of the tree, and is determined by the designation of an outgroup. The outgroup is an organism that you are confident is most distantly related to everything else in your tree. Outgroup selection is not a trivial task, but to simplify it here, we suggest always using an Archaeal 16S rDNA sequence as your outgroup.