# W85 Annotation
This repository stores all of my work relating to the TE annotation of W85, a diploid blueberry genome. The complete [EDTA](https://github.com/oushujun/EDTA) pipeline was run wtih a provided CDS FASTA file using the `--cds` flag and used RepeatModeler to identify remaining TEs using the `--sensitive 1` option; default options were used for stages other than generating a whole-genome annotation with the `--anno 1` flag. The script for running EDTA can be located at `src/Annotate_W85_TEs_EDTA.sb`.

# Installation:
I prefer to use [EDTA](https://github.com/oushujun/EDTA) by Shujun Ou to generate my TE annotations. EDTA installation directions can be found there.

# Output Data:
I have not uploaded the output data to GitHub due to the nature of GitHub and the file sizes. However should you run this code it will output data to `results/EDTA_Annotation`.
Principal outputs are `results/EDTA_Annotation/Vce1.0.fasta.mod.EDTA.TEanno.gff3` and `results/EDTA_Annotation/Vce1.0.fasta.mod.EDTA.TEanno.sum`; the former is the whole-genome annotation and the latter is a summary file describing the relative portions of TEs.

For a quick perusal of the annotation, the TE type can be easily gleaned from the third column, e.g `Gypsy_LTR_retotransposon`. However for a more complete representation of the TE type, look to the last column which uses a naming scheme similar to the one proposed in [Wicker 2007](https://www.nature.com/articles/nrg2165).

The most salient portion of the annotation file is contained within a substring of the last column between the strings `;Classification=` and `;`, e.g: `;Classification=LTR/Gypsy;`, where the entries are placed in TE Order and TE Superfamily notation separated by the `/` string. In the case where the TE's Order was unable to be determined, there is no `/` substring and the entry will just be `;Classification=Unknown;`. Take care when parsing the strings to distinguish the unknown superfamilies of an LTR element vs a LINE element, as they both have `unknown` for the superfamily value and if you are grouping these it may lead to incorrect interpretation if unaware.
