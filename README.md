# angiosperm-traits

This project contains data files and source code for the comparative analysis of
binary traits in flowering plants in the context of [phylogenetic](https://github.com/FePhyFoFum/big_seed_plant_trees/releases/tag/v0.1) 
[generalized linear modeling](https://github.com/naturalis/trait-geo-diverse/blob/master/doc/lm.Rmd). 
The general idea is that 
[OMI-transformed](https://github.com/rvosa/sdmdl-angiosperm-data/blob/master/script/OMI.R)
[values](https://raw.githubusercontent.com/rvosa/sdmdl-angiosperm-data/master/data/niche_traits_merged.csv)
for 
[GIS data](https://drive.google.com/drive/u/0/folders/1EFPurfyxhClDBsxjEAXf00A3LL2MrkQw) 
at 
[curated](https://github.com/rvosa/sdmdl-angiosperm-data/blob/master/script/coordinate_cleaner.R)
[localities](https://github.com/rvosa/sdmdl-angiosperm-data/tree/master/data/occurrences) 
are the predictors for three traits:

1. [Woodiness](https://github.com/rvosa/sdmdl-angiosperm-data/blob/master/data/woody.nex) - in this
   matrix, the character can occupy three states (derived woody, non-woody, ancestral woody). Derived 
   woodiness can evolve from non-woody plants. So we collapsed it into a binary trait (derived versus 
   non-woody) by deleting ancestral woody.
2. [Mycorrhiza](https://github.com/rvosa/sdmdl-angiosperm-data/blob/master/data/myco.nex) - in this
   matrix, the character has four states (only arbuscular, only ecto, both, or neither). The arbuscular 
   mycorrhiza (AM) type is the ancestral state, out of which ectomycorrhiza, both, or neither can 
   evolve. Thus, AM is one state, and EM + both + neither are combined into one state. 
3. [Domestication](https://github.com/rvosa/sdmdl-angiosperm-data/blob/master/data/crops.tsv) - here
   we have three states: 1) the plant is ancestral to a domesticated crop (e.g. teosinte), 2) the
   plant only exists as domesticate (e.g. mayze), 3) the wild plant is used as a crop, more or less
   unchanged (e.g. Dioscorea sp.). We combine state 1 and 3 and omit 2 from the data, as domesticated 
   plants is already a bridge too far for our research question. We then take other non-domesticated 
   species from the ALLMB.tre as the background (state 0).

Things done/to do:

1. Recode dependent characters to binary states. Mostly done just for technical reason, but also to 
   shape the exact test that we are trying to do. 
2. Correct for collinearity in the predictor characters, based on the variance inflation factor - 
   using the vif() function of the usdm package. 
3. Model selection, i.e. which predictors go in the formula for the selected dependent variable - 
   using the phylostep() function of the phylolm package. 
4. Check the best models for the assumptions that are made when performing generalized linear modeling 
   - using the check_model() function of the performance package. 
5. Model optimization to check the significance of the best models - using the phyloglm() function of 
   the phylolm package.
