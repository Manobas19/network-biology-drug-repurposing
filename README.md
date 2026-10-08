# Network Biology and Drug Repurposing with Multiomics

A Google Colab notebook for integrating expression, somatic mutation and optional proteomics evidence, analyzing biological networks, and prioritizing drug repurposing hypotheses.

## Run in Google Colab

Upload `Network_Biology_Drug_Repurposing_Multiomics_Colab.ipynb` to https://colab.research.google.com/ and select **Runtime → Run all**. A CPU runtime is sufficient for the small demonstration.

Default `MODE = "demo"` generates synthetic sample data automatically. Installation requires internet access. Demo results are not biological findings. The notebook has not been executed in Colab.

## Workflow

1. Generate demo inputs or upload processed real data.
2. Validate expression, mutation, protein and network identifiers.
3. Integrate molecular evidence and calculate network communities and centrality.
4. Perform pathway enrichment with a measured-gene background.
5. Map curated drug-target evidence.
6. Calculate degree-matched network proximity and expression-signature reversal.
7. Rank research candidates and export CSV, GraphML, plots and a reproducibility manifest.

## Python dependencies

NumPy, pandas, SciPy, NetworkX, Matplotlib, requests, GSEApy and gprofiler-official. The first notebook cell installs dependencies; the final export records installed versions.

## Resources

STRING, TCGA/GDC, cBioPortal, Enrichr, Gene Ontology, Reactome, KEGG, g:Profiler, DGIdb, Open Targets, LINCS and Cytoscape. Some resources are accessed through optional live helpers; DGIdb/Open Targets evidence and LINCS signatures use standardized input exports. These are not all Python packages. The notebook does not depend on a live CLUE query service.

## Real-data inputs

Set `MODE = "real"` and use the notebook upload cell. Inputs go into `multiomics_inputs/real/`.

| Required file | Columns |
|---|---|
| expression_de.csv | gene, log2FC, pvalue, padj |
| samples.csv | sample_id, group, mutation_profiled |
| mutations.csv | sample_id, gene, variant_class |
| ppi_edges.csv | source, target, score |
| drug_targets.csv | drug_id, drug_name, gene, action, source, reference |
| signatures.csv | signature_id, drug_id, gene, z, cell_line, dose, time |
| provenance.csv | file, source, release, cohort, notes |

Optional: `proteomics_de.csv`, `open_targets.csv`, and `pathways.gmt`. Detailed contracts are in the notebook. Use consistent human HGNC gene symbols and stable drug identifiers. Expression data must include all tested genes. Raw FASTQ processing and count-based differential expression are outside this notebook's scope.

## Interpretation

Synthetic compounds and genes demonstrate software only. Real-data scores are heuristic research priorities, not clinical recommendations, efficacy estimates or CMap tau. Account for cohort selection, assay coverage, network bias, signature context and interaction mechanisms. Validate candidates independently.

## Outputs

Ranked drug candidates, gene priorities, network modules, enrichment tables, signature reversal results, target coverage, Cytoscape-compatible GraphML, plots, input snapshots, package versions and checksums.
