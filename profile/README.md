# Platforma Open

Open-source analysis and decision-making blocks for [Platforma](https://platforma.bio/), a biologics discovery platform by [MiLaboratories](https://github.com/milaboratory).

Platforma connects sequencing, experimental, structural, functional, and developability data to biologics discovery decisions. Its modular blocks support antibody discovery, TCR discovery, peptide discovery, immune repertoire analysis, single-cell RNA-seq, bulk RNA-seq, and multiomics workflows.


**New to Platforma?** [Download the desktop app and server](https://platforma.bio/downloads) · [Documentation](https://docs.platforma.bio/) · [Build your own block](https://github.com/milaboratory/platforma)

---

## What can Platforma be used for?

Platforma provides modular workflows for analyzing biological data and supporting decisions across biologics discovery and immune research.

- **Antibody discovery:** Analyze antibody and BCR sequencing data, identify enriched clones, investigate clonal lineages and affinity maturation, evaluate sequence and structural liabilities, and prioritize candidates for further testing.
- **TCR discovery:** Analyze TCR repertoires, identify clonotypes, cluster sequences by similarity or predicted specificity, and integrate repertoire and experimental data.
- **Peptide discovery:** Analyze peptide display and selection data to identify enriched peptide sequences and prioritize candidates.
- **Immune repertoire analysis:** Analyze BCR and TCR repertoires, including clonotyping, diversity, V/J gene usage, clonotype abundance, convergence, generation probability, and somatic hypermutation.
- **Single-cell and multiomics:** Integrate V(D)J sequencing with single-cell RNA-seq, antigen-binding measurements, and other cellular annotations.
- **Bulk RNA-seq:** Perform read mapping, differential expression, pathway analysis, and interactive exploration of gene expression data.

---

## How blocks work

A Platforma project is a sequence of blocks. Each one reads the outputs of the blocks before it and publishes columns the blocks after it can use — abundances, scores, cluster assignments, annotations — so an analysis is assembled by connecting steps rather than by writing glue code.

Every block has three parts: a **workflow** describing the computation, a **model** declaring what it consumes and produces, and a **UI**. Because outputs are typed columns rather than files, a score computed anywhere in a project is available everywhere downstream. That is why, for example, a liability flag can be overlaid on a UMAP produced by a different block, or an enrichment score can rank candidates in a selection step three blocks later.

Blocks are installed from the marketplace inside the Platforma app. You do not clone these repositories to use them — they are here so you can read exactly what each analysis does, cite the right tools, file issues, and build your own.

---

## The blocks

### Getting data in

| Block | What it does |
|---|---|
| [Samples & Data](https://github.com/platforma-open/samples-and-data) | Import raw data — FASTQ, FASTA, count matrices, H5AD, Seurat objects, CSV/TSV — and attach sample metadata. The first block in most projects. |
| [Import V(D)J Data](https://github.com/platforma-open/import-vdj-data) | Load clonotype tables from MiXCR, ImmunoSeq, QIAseq, Cell Ranger, AIRR, or custom CSV/TSV |
| [Import Assay Data](https://github.com/platforma-open/immune-assay-data) | Join binding, affinity, or specificity measurements onto clonotypes by sequence alignment |
| [Import scRNA-seq Data](https://github.com/platforma-open/import-sc-rnaseq-data) | Load single-cell count matrices from CSV/TSV |
| [Import Bulk Count Matrix](https://github.com/platforma-open/import-bulk-count-matrix) | Load a bulk RNA-seq count matrix |
| [CSV/TSV Import](https://github.com/platforma-open/xsv-import) | Import arbitrary delimited tables |
| [FASTQ Demultiplexing](https://github.com/platforma-open/demultiplex-fastq) | Split a multiplexed FASTQ dataset into per-sample reads by barcode |
| [FASTQ Reader](https://github.com/platforma-open/fastq-reader) | Inspect raw reads of an imported dataset, one sample at a time |
| [FastQC](https://github.com/platforma-open/fastqc) | Read-level quality control with FastQC |

### Clonotyping and library profiling

| Block | What it does |
|---|---|
| [MiXCR Clonotyping](https://github.com/platforma-open/mixcr-clonotyping) | Extract TCR and BCR clonotypes from raw sequencing data against germline references |
| [MiXCR Amplicon Alignment](https://github.com/platforma-open/mixcr-amplicon-alignment) | Align synthetic library amplicons against a reference construct you supply |
| [MiXCR scFv Alignment](https://github.com/platforma-open/mixcr-scfv-clonotyping) | Clonotype scFv libraries, separating VH, linker, and VL |
| [MiXCR library builder](https://github.com/platforma-open/mixcr-library-builder) | Build custom MiXCR reference libraries for non-standard species or novel alleles |
| [Cellecta DriverMap™ AIR Clonotyping](https://github.com/platforma-open/cellecta-drivermap-air-mixcr-clonotyping) | Clonotyping for the Cellecta DriverMap AIR TCR-BCR Profiling Kit v2 |
| [Peptide Profiling](https://github.com/platforma-open/peptide-extraction) | Extract peptide sequences from phage, yeast, or mRNA display selection reads |
| [Amplicon Profiling](https://github.com/platforma-open/synthetic-repertoire-profiler) | Profile synthetic amplicon libraries against parent sequences and call mutations |
| [Redefine Clonotypes](https://github.com/platforma-open/redefine-clonotypes) | Re-group an existing dataset under a different clonotype definition |

### Repertoire analysis

| Block | What it does |
|---|---|
| [Diversity Analysis](https://github.com/platforma-open/repertoire-diversity) | Richness (Chao1, Efron-Thisted), evenness (Shannon-Wiener, Inverse Simpson), and dominance (D50, Gini) with depth normalization |
| [Rarefaction Analysis](https://github.com/platforma-open/rarefaction) | Rarefaction curves for depth-fair diversity comparison |
| [Distance Analysis](https://github.com/platforma-open/repertoire-distance) | Pairwise repertoire similarity via F1, F2, Jaccard, and correlation metrics |
| [V/J Gene Usage](https://github.com/platforma-open/vj-gene-usage) | V and J segment usage frequencies and V–J pairing biases |
| [CDR3 Spectratype](https://github.com/platforma-open/cdr3-spectratype) | CDR3 length distributions, for detecting clonal expansions |
| [Clonotype Distribution](https://github.com/platforma-open/clonotype-distribution) | Clonal abundance across tissues, timepoints, and subjects |
| [Differential Abundance](https://github.com/platforma-open/differential-clonotype-abundance) | Identify differentially abundant clonotypes or peptides between conditions |
| [MiXCR SHM Trees](https://github.com/platforma-open/mixcr-shm-trees) | Somatic hypermutation lineage trees, with sequence search and baskets |
| [Generation Probability](https://github.com/platforma-open/generation-probability) | Pgen per clonotype via OLGA — clonal rarity and germline distance |
| [Clonotype Convergence](https://github.com/platforma-open/clonotype-convergence) | Detect antigen-driven convergence in BCR repertoires (STAR) |

### Candidate analysis and selection

| Block | What it does |
|---|---|
| [Enrichment Analysis](https://github.com/platforma-open/clonotype-enrichment) | Score sequence enrichment across selection rounds or conditions to identify candidates and biological signals associated with selection.
| [Sequence Browser](https://github.com/platforma-open/clonotype-browser) | Browse sequences across samples and annotate them with reproducible rules |
| [Sequence Space](https://github.com/platforma-open/clonotype-space) | Project a whole library to a 2D UMAP, colored by any upstream property |
| [Sequence Embeddings](https://github.com/platforma-open/sequence-embeddings) | Protein language model vectors — universal (ESM-2) or format-specialist |
| [Sequence Clustering](https://github.com/platforma-open/clonotype-clustering) | Cluster by sequence identity or BLOSUM similarity (MMseqs2) |
| [Embedding Clustering](https://github.com/platforma-open/embedding-clustering) | Cluster by distance in embedding space (HDBSCAN) |
| [Paratope Clustering](https://github.com/platforma-open/paratope-clustering) | Cluster antibodies on predicted antigen-contact residues (Parapred) |
| [3D Structure Clustering](https://github.com/platforma-open/3d-structure-clustering) | Cluster predicted structures by shape (Foldseek) |
| [Repertoire Score](https://github.com/platforma-open/repertoire-score) | Transparent composite score combining maturation, abundance, convergence, and rarity to support antibody candidate prioritization.
| [Lead Selection](https://github.com/platforma-open/antibody-tcr-lead-selection) | Filter, rank, and diversify antibody and TCR candidates to generate a final candidate panel for further testing.

### Developability

| Block | What it does |
|---|---|
| [Sequence Liabilities](https://github.com/platforma-open/antibody-sequence-liabilities) | Flag deamidation, isomerization, glycosylation, oxidation, and cysteine liabilities, classified by fixability |
| [Humanness Score](https://github.com/platforma-open/humanization-score) | OASis humanness score against natural human antibody repertoires |
| [Sequence Properties](https://github.com/platforma-open/sequence-properties) | Charge, pI, GRAVY, molecular weight, extinction coefficient, and more |
| [3D Structure Prediction](https://github.com/platforma-open/3d-structure-prediction) | Predict antibody and nanobody structures with ImmuneBuilder |
| [3D Structure-Based Liabilities](https://github.com/platforma-open/3D-Structure-Based-Liabilities) | Structure-aware liabilities and surface metrics (TAP, TNP) |

### Specificity, function, and integration

| Block | What it does |
|---|---|
| [ImmuneWatch DETECT](https://github.com/platforma-open/immunewatch-detect) | TCR specificity annotation |
| [GLIPH2 Clustering](https://github.com/platforma-open/tcr-clustering-gliph2) | Group TCRs likely to recognize the same antigen |
| [ImmunoMatch](https://github.com/platforma-open/immuno-match) | Predict cognate heavy–light chain pairing |
| [Feature Barcode Profiling](https://github.com/platforma-open/feature-integration) | Assign antigens to single cells from BEAM or LIBRA-seq reads |
| [Clonotype Multiomic Integration](https://github.com/platforma-open/vdj-multiomic-integration) | Bring single-cell antigen binding and cell annotations onto clonotypes |
| [VDJ Integration](https://github.com/platforma-open/vdj-integration) | Match clonotypes between two datasets to carry paired chains and annotations across |
| [Tite-Seq Analysis](https://github.com/platforma-open/titeseq-analysis) | Estimate apparent binding affinity from Tite-Seq reads |
| [Deep Mutational Scanning](https://github.com/platforma-open/repertoire-mutation-heatmap) | Position × residue mutation-enrichment heatmaps over DMS libraries |

### Single-cell RNA-seq

| Block | What it does |
|---|---|
| [Cell Ranger](https://github.com/platforma-open/cell-ranger) | Preprocess scRNA-seq FASTQ into count matrices |
| [Dimensionality Reduction](https://github.com/platforma-open/dimensionality-reduction) | PCA, t-SNE, and UMAP, with optional Harmony batch correction |
| [Batch Correction](https://github.com/platforma-open/batch-correction) | ComBat and Harmony batch correction |
| [Leiden Clustering](https://github.com/platforma-open/leiden-clustering) | Identify cell populations by Leiden clustering |
| [Cell Type Annotation](https://github.com/platforma-open/cell-type-annotation) | Annotate cell types with CellTypist, with confidence scores |
| [Cluster Markers](https://github.com/platforma-open/cluster-markers) | Marker genes distinguishing clusters (Wilcoxon rank-sum) |
| [Differential Expression (Single Cell)](https://github.com/platforma-open/sc-differential-expression) | Differential expression between cell groups |
| [Compositional Analysis](https://github.com/platforma-open/compositional-analysis) | Cell type proportion changes across conditions (scCODA) |
| [Pseudotime Inference](https://github.com/platforma-open/pseudotime-inference) | Order cells along trajectories with PAGA and DPT |
| [Cell Browser](https://github.com/platforma-open/cell-browser) | Explore UMAP embeddings and gene expression interactively |

### Bulk RNA-seq

| Block | What it does |
|---|---|
| [STAR Read Mapping](https://github.com/platforma-open/star-read-mapping) | Align reads with STAR, count genes with featureCounts |
| [Differential Expression](https://github.com/platforma-open/differential-expression) | DESeq2 differential expression with configurable thresholds |
| [Functional Analysis](https://github.com/platforma-open/functional-analysis) | Pathway enrichment over Gene Ontology and Reactome (clusterProfiler) |
| [Gene Browser](https://github.com/platforma-open/gene-browser) | Explore gene expression with box plots and heatmaps |

### Visualization and utilities

| Block | What it does |
|---|---|
| [Graph Maker](https://github.com/platforma-open/graph-maker) | Plot any column from any block — 28 chart types, with significance testing |
| [Table](https://github.com/platforma-open/table) | Table view over data from other blocks |
| [BLAST Local Database](https://github.com/platforma-open/blast) | BLAST search against your own local database |
| [GPU Detection](https://github.com/platforma-open/gpu-test) | Report GPU availability, drivers, and benchmarks |

---

## Built on open science

These blocks wrap and credit the tools the field already relies on — among them MMseqs2, UMAP, HDBSCAN, OLGA, ImmuneBuilder, ANARCI, Foldseek, Parapred, promb/OASis, ESM-2, DESeq2, scCODA, CellTypist, STAR, FastQC, Kalign, Biopython, and MiXCR. Each block's README and in-app description names the tools it uses and the publications to cite. If a block contributed to your results, please cite the underlying method as well as Platforma.

## Example biologics discovery workflows

Platforma blocks can be combined to build end-to-end workflows for biologics discovery.

### In vitro antibody discovery

A typical workflow can combine sequencing and display analysis, clonotyping, enrichment analysis, sequence clustering, structural analysis, developability assessment, and candidate selection.

### In vivo antibody discovery

A typical workflow can combine BCR repertoire sequencing, clonotype analysis, somatic hypermutation lineage trees, convergence analysis, generation probability, developability analysis, and candidate prioritization.

### TCR discovery

A typical workflow can combine TCR clonotyping, repertoire analysis, GLIPH2 clustering, specificity annotation, and experimental data integration.

### Peptide discovery

A typical workflow can combine peptide extraction, selection/enrichment analysis, sequence clustering, and candidate prioritization.

## Documentation

- **[docs.platforma.bio](https://docs.platforma.bio/)** — user guides and SDK reference
- **[Antibody discovery guides](https://docs.platforma.bio/biology-guides/antibody-discovery/)** — end-to-end workflows for discovery campaigns
- **[V(D)J analysis guides](https://docs.platforma.bio/biology-guides/vdj-analysis/)** — immune repertoire workflows
- **[Block development](https://docs.platforma.bio/)** — how to build a block of your own

## Build a block

Blocks are TypeScript and Tengo, built against the **[Platforma SDK](https://github.com/milaboratory/platforma)**. If an analysis you need is missing, the SDK and any block in this organization are a working reference for adding it — the model, workflow, and UI of every block here are readable in full.

## Getting Platforma

The desktop app and server are available from **[platforma.bio/downloads](https://platforma.bio/downloads)** for macOS, Windows, and Linux, plus Docker. Academic researchers can request a **[free license](https://platforma.bio/academic-access)**. Commercial teams can request a **[demo](https://platforma.bio/request-demo)**.

## Platforma and MiXCR

Platforma and MiXCR are complementary tools developed by MiLaboratories.

[MiXCR](https://github.com/milaboratory/mixcr) is an immune repertoire sequencing analysis toolkit for processing and analyzing TCR and BCR sequencing data, including V(D)J alignment and clonotype assembly.

Platforma provides a modular environment for combining MiXCR results with other biological analyses, experimental measurements, and decision workflows. MiXCR output can be used as input to Platforma blocks such as repertoire analysis, SHM trees, generation probability, convergence analysis, and candidate selection.

## Support

Issues and feature requests belong on the individual block repositories. For anything else, contact [support@milaboratories.com](mailto:support@milaboratories.com).
