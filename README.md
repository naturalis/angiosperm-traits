# angiosperm-traits

This project contains data files and source code for the comparative analysis of
binary traits in flowering plants in the context of [phylogenetic](https://github.com/FePhyFoFum/big_seed_plant_trees/releases/tag/v0.1) generalized
linear modeling. The general idea is that 
[OMI-transformed](https://github.com/rvosa/sdmdl-angiosperm-data/blob/master/script/OMI.R)
[values](https://raw.githubusercontent.com/rvosa/sdmdl-angiosperm-data/master/data/niche_traits_merged.csv)
for 
[GIS data](https://drive.google.com/drive/u/0/folders/1EFPurfyxhClDBsxjEAXf00A3LL2MrkQw) 
at 
[curated](https://github.com/rvosa/sdmdl-angiosperm-data/blob/master/script/coordinate_cleaner.R)
[localities](https://github.com/rvosa/sdmdl-angiosperm-data/tree/master/data/occurrences) 
are the predictors for three traits:

1. [Woodiness](https://github.com/rvosa/sdmdl-angiosperm-data/blob/master/data/woody.nex) - in this
   matrix, the character can occupy three states (derived woody, non-woody, ancestral woody), which
   we may want to collapse a binary trait (derived versus non-derived) by lumping everything that
   is not secondary woody.
2. [Mycorrhiza](https://github.com/rvosa/sdmdl-angiosperm-data/blob/master/data/myco.nex) - in this
   matrix, the character has four states (only arbuscular, only ecto, both, or neither). Perhaps we
   need to collapse these, but the question is how to do this best. Presumably, Vincent Merckx can 
   tell us which of the two (AM or EM) is most interesting as a derived state whose appearance we
   want to explain.
3. [Domestication](https://github.com/rvosa/sdmdl-angiosperm-data/blob/master/data/crops.tsv) - here
   we have three states: 1) the plant is ancestral to a domesticated crop (e.g. teosinte), 2) the
   plant only exists as domesticate (e.g. mayze), 3) the wild plant is used as a crop, more or less
   unchanged (e.g. Dioscorea sp.). We probably keep 1+3 and omit 2 from the data. We then take
   other species from the other two data sets (woody/myco) as the background of undomesticated
   species.
