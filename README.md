# Key metabolic genes for relevant biogeochemical functions

This repository contains a manually curated table of key metabolic genes associated with major biogeochemical functions. The genes included here were selected as representative marker genes for the corresponding metabolic pathways.

The table is intended to be used together with functional annotation outputs from tools such as **KofamKOALA** and **BlastKOALA**.

## Table structure

| Column              | Purpose                                                       |
| ------------------- | ------------------------------------------------------------- |
| `KO`                | KEGG Orthology identifier, e.g. `K10944`                      |
| `Cycle`             | Broad biogeochemical cycle, e.g. Carbon, Nitrogen, Sulfur     |
| `Pathway`           | Name of the metabolic pathway or process                      |
| `Pathway_ID`        | Unique short identifier used in downstream analyses and plots |
| `Function`          | Functional description of the marker                          |
| `Gene_abbreviation` | Standard gene abbreviation, e.g. `amoA`, `nirK`               |
| `Enzyme`            | Enzyme name                                                   |

## Recommended workflow

Each entry is linked to a KEGG Orthology (KO) identifier and assigned to a biogeochemical cycle, metabolic pathway, and functional category.

The recommended workflow is as follows:

1. **Annotate proteins with KO identifiers**

   Annotate predicted proteins using **KofamKOALA** and/or **BlastKOALA** to obtain KO assignments for each protein sequence.

2. **Apply annotation-quality filtering**

   KofamKOALA results should be filtered using the profile-specific score thresholds provided by KOfam. When multiple candidate annotations are available, annotation score and E-value should be considered to retain the most strongly supported hit.

3. **Match recovered KOs against the curated marker-gene table**

   The KO identifiers recovered from the annotation should be matched against the `KO` column of this table.

4. **Use `Pathway_ID` as the common downstream identifier**

   `Pathway_ID` should be used as the stable identifier for downstream summaries and visualizations. Multiple genes or KO identifiers representing the same metabolic process can therefore be grouped consistently under the same pathway identifier.

5. **Summarize results**

   For each genome, MAG, metagenome, or sample, summarize whether individual marker genes and metabolic pathways were recovered. Depending on the analysis, summaries may represent presence/absence, number of indentified markers, gene abundance, or normalized abundance.

7. **Generate pathway-level plots**

   Plotting should use `Pathway_ID` as the primary pathway identifier, while descriptive information such as `Pathway`, `Cycle`, or `Gene_abbreviation` can be used for labels, legends, or grouping.

#### Important note on metabolic-function validation

The presence of a single marker gene is not equivalent to the presence of a complete metabolic pathway or function

For more robust validation, metabolic functions should be assessed by considering the recovery of additional sub-units belonging to the same enzymatic complex, where applicable, as well as multiple enzymes representing different steps of a broader metabolic pathway.

Complementary metabolic annotation frameworks, such as **DRAM**, can also be used to provide broader pathway context and support the interpretation of individual marker-gene assignments.

## Future development

Future versions of this repository will include a custom script to automate KO matching, annotation filtering, integration with this curated table, pathway-level summarization, and generation of standardized plots using R
