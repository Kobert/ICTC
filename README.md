# ICTC
Supplementary data and software for "Computing the Internode Certainty and related measures from partial gene trees." 

-----------------------------------------------------------
data:

data/Example
 contains the tree files for the presented, simple example
  - Reference tree
  - (Partial )Tree set

data/Reduced
 contains reduced data sets based on the yeast data set. 
 Folder names denote the p parameter of the geometric distribution used for obtaining the tree sets (i.e. P01 represents p=0.1).
 Each such folder contains 
  - a set of all resulting trees (4-23 taxa)
  - a set restricted to trees with a partial taxon set.

data/Empirical
 contains the avian and yeast data: 
  - reference tree 
  - the set of all trees with comprehensive taxon sets 
  - the set of all trees with fewer taxa than the reference tree
  - the combination of comprehensive and partial trees.

-------------------------------------------------------------
software:

contains 
- the implementation of the probabilistic, along with the lossless adjustment scheme
- the proof of concept implementation of the observed adjustment scheme.

-------------------------------------------------------------
To compile RAxML (under Linux), simply use any of the makefiles, e.g:

"make -f Makefile.gcc"

in the respective folders (here software/LosslessAndProbabilistic, or software/Observed).

To calculate the Internode certainty for a reference tree, given a collection of (partial) trees (here the yeast data set), call RAxML as follows:

"./raxmlHPC -f i -t ../../data/Empirical/Yeast/yeast_reference.tre -z ../../data/Empirical/Yeast/yeast_all.tre -m GTRCAT -n NAME"

- "raxmlHPC" must be replaced with the correct file if another makefile (other than Makefile.gcc) is used.
- "-f i" calls the Internode certainty calculation.
- "-t ../../Empirical/Yeast/data/yeast_reference.tre" and  "-z ../../data/Empirical/Yeast/yeast_all.tre" must be the path to the reference tree and (partial) tree collection respectively.
- "-n NAME", NAME must be a unique identifier for every analysis. 

---------------------------------------------------------------
To obtain additional information during the analysis or to verify the values presented in the various tables, uncomment the first line (i.e. "#define _DEBUG_PARTIAL_IC") of bipartitionList.c and recompile.

---------------------------------------------------------------

