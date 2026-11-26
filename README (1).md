# In Silico Drug Repurposing for Schizophrenia: Molecular Docking of Antipsychotic Compounds Against Hub-Gene Targets

A computational drug-repurposing study: 42 known compounds were filtered for drug-likeness and predicted ADMET properties, and the 13 that passed were docked against schizophrenia-associated hub-gene targets. Lumateperone, an approved antipsychotic, had the best predicted binding on the two targets reported here (KCNA1 and ATP2B2).

## Aim

To find existing compounds that may interact with proteins encoded by genes linked to schizophrenia, as a starting point for repurposing.

## Methods

1. **Targets:** Ten hub genes (BDNF, VEGFA, PVALB, KCNA1, KCNA2, GRIN2A, ATP2B2, APOE, PPARGC1A, SCN1A) were taken from Wang et al., *Schizophrenia* 10, 64 (2024). I did not identify these genes myself. Protein structures were downloaded from the PDB.
2. **Ligands:** 32 synthetic compounds (DrugBank, PubChem) and 10 natural phytocompounds (literature, PubChem): 42 in total.
3. **Drug-likeness and ADMET:** Predictions from admetSAR and Molsoft. Compounds were kept if they passed Lipinski, Veber and Ghose rules and were predicted non-AMES-toxic and non-carcinogenic. 13 compounds passed.
4. **Clustering:** PCA and K-means clustering on the ADMET/physicochemical descriptors. The 13 rule-passing compounds grouped together as drug-like, consistent with the rule-based filter.
5. **Docking:** Ligands were energy-minimised (UFF) in PyRx and docked with AutoDock Vina. Proteins were prepared in BIOVIA Discovery Studio Visualizer. Grid boxes were set from known binding-site residues for 2KNE (ATP2B2) and 1EXB (KCNA1).
6. **Interaction analysis:** Poses were analysed in BIOVIA Discovery Studio.
7. **Reference comparison:** Lumateperone was compared with xanomeline and trospium chloride, the components of the approved drug Cobenfy.

## Key results

- 42 compounds screened, 13 shortlisted (all synthetic).
- Lumateperone had the lowest (best) docking energy among the 13 on both reported targets:

| Compound | ATP2B2 (2KNE), kcal/mol | KCNA1 (1EXB), kcal/mol |
|---|---|---|
| **Lumateperone** | **-9.5** | **-9.7** |
| Loxapine | -8.5 | -7.0 |
| Melperone | -7.7 | -7.9 |
| Cariprazine | -7.5 | -7.8 |
| Clozapine | -8.0 | -7.0 |
| Amitriptyline | -8.0 | -7.1 |

- admetSAR predicted lumateperone to cross the blood-brain barrier and be well absorbed in the intestine, and to be non-AMES-toxic and non-carcinogenic.

Full scores, figures and interaction diagrams are in the folders below.

## Repository contents

- `results/docking_scores.csv`: docking energies for all 13 compounds
- `figures/pca_plot.png`: PCA of the 42 compounds (drug-like vs non-drug-like)
- `figures/binding_energy_comparison.png`: binding energies against ATP2B2 and KCNA1
- `figures/kcna1_lumateperone_interactions.png` and `figures/atp2b2_lumateperone_interactions.png`: 2D interaction diagrams
- `report.pdf`: full write-up (add only if your college/guide allows)

## Limitations

- Docking scores are rough predictions and are known to give false positives. No experimental validation has been done.
- The 1EXB structure is the cytoplasmic Kvβ2 subunit bound to the Kv1.1 T1 domain, not the pore-forming part of the channel, so the docking result applies to that assembly.
- The docking protocol was not validated by re-docking a co-crystallised ligand. The comparison with xanomeline and trospium chloride is a reference check, not a validation.
- Docking was run against ten targets, but only ATP2B2 and KCNA1 are reported here.
- No molecular dynamics simulation was performed.

## Tools

PyRx, AutoDock Vina, BIOVIA Discovery Studio Visualizer, admetSAR, Molsoft, PubChem, DrugBank, RCSB PDB, Python (PCA/K-means).

## Author

Shivani S Banad, B.E. Biotechnology, Ramaiah Institute of Technology
LinkedIn: linkedin.com/in/shivani-banad
