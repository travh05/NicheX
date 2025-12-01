# marrow-niche-cross-species

This project compares mouse and human bone marrow stromal niches using public single-cell RNA-seq datasets.

## Structure

```text
marrow-niche-cross-species/
  data/
    mouse/    # mouse stromal atlas (e.g., GSE128423)
    human/    # human marrow stromal datasets
  notebooks/
    01_mouse_preprocessing.ipynb
    02_mouse_markers_and_annotation.ipynb
    03_human_preprocessing.ipynb
    04_human_markers_and_annotation.ipynb
    05_cross_species_mapping.ipynb
    06_pathways_and_ligand_receptor.ipynb
  results/
    figures/
    tables/
  env.yml
  README.md
