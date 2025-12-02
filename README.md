# NicheX

Cross-species map of the mouse and human bone marrow stromal niche.

NicheX builds a reproducible pipeline that:

* preprocesses mouse and human bone marrow stromal scRNA-seq datasets
* defines stromal / endothelial niches and their marker genes
* maps mouse ↔ human niche archetypes using one-to-one orthologs
* prepares summary tables and figures for downstream pathway / ligand–receptor work

---

## What is included

* `notebooks/`
  * `01_mouse_preprocessing.ipynb`  
    Load Baryawno et al. mouse bone marrow stroma (GSE128423), subset stromal cells, QC, normalization, clustering, UMAP.
  * `02_mouse_markers_and_annotation.ipynb`  
    Compute per-cluster marker genes, inspect canonical markers (Lepr, Cxcl12, Col1a1, etc.), and export mouse stromal cell-type marker tables.
  * `03_human_preprocessing.ipynb`  
    Load the Bandyopadhyay et al. human bone marrow atlas (GSE253355), subset stromal / endothelial / perivascular populations, and harmonize annotations.
  * `04_human_markers_and_annotation.ipynb`  
    Compute marker genes per human niche cell type and export marker tables.
  * `05_cross_species_mapping.ipynb`  
    Join mouse and human marker tables through a one-to-one ortholog table, compute overlap metrics, and build mouse↔human niche correspondence summaries.
  * `06_pathways_and_ligand_receptor.ipynb`  
    Placeholder for downstream pathway and ligand–receptor analysis on conserved / species-specific niches.

* `data/`
  * `mouse/`  
    Local copy of GSE128423 10x matrices and processed mouse stromal `.h5ad` files (not tracked in git).
  * `human/`  
    Seurat `.rds` or converted `.h5ad` files for GSE253355, and any derived stromal-only objects (not tracked in git).
  * `orthologs/`  
    Mouse–human one-to-one ortholog table exported from Ensembl / BioMart.

* `results/`
  * `figures/` – UMAPs, marker plots, and heatmaps for cross-species mapping.
  * `tables/` – CSVs with:
    * per-cell-type marker genes in mouse and human
    * marker summary stats per cell type
    * cross-species overlap / mapping metrics.

* `env.yml`  
  Conda environment file for reproducing the Python analysis stack (scanpy, anndata, pandas, matplotlib, seaborn, etc.).

---

## What is not included

Large raw and processed datasets are not committed to this repository.  
Download them locally before running the notebooks.

* Mouse stromal atlas (Baryawno et al. 2019) – **GSE128423**  
  A cellular taxonomy of the bone marrow stroma in homeostasis and leukemia.  
  GEO: https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE128423

* Human bone marrow atlas (Bandyopadhyay et al. 2024) – **GSE253355**  
  Mapping the cellular biogeography of human bone marrow niches.  
  GEO: https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE253355

* Mouse–human ortholog table  
  Exported from Ensembl / BioMart (e.g. one-to-one orthologs between *Mus musculus* and *Homo sapiens*).

A minimal `.gitignore` to keep the repo lightweight:

```gitignore
.DS_Store
.ipynb_checkpoints/
__pycache__/

data/
*.h5ad
*.mtx
*.mtx.gz
*.tsv.gz
*.csv.gz
