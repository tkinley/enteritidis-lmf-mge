# Lineage-aware comparative genomics shows no consistent reservoir-specific plasmidome in low-moisture food associated *Salmonella* Enteritidis

Code, curated metadata, and supplementary tables for:

> Tenzin K, Balyatanda SB, Prakash SDP, Siliveru K, Platt TG (2026). *Food Research International* 242: 120003. [https://doi.org/10.1016/j.foodres.2026.120003](https://doi.org/10.1016/j.foodres.2026.120003)

If you reuse code or tables, please cite the paper.

## Question

Do *S.* Enteritidis from low-moisture foods (nuts, spices, grains) carry a distinct plasmidome compared with non-LMF (poultry/egg) isolates? Plasmid content is lineage-structured, so this study compares reservoirs **within shared lineages** (SNP cluster stratification).

## Main finding

**No consistent LMF-specific plasmidome after lineage control.** Variation was structured by lineage, not reservoir.

![Summary figure](results/figures/README_summary_figure.png)

## Key results

| Metric | Value |
|---|---|
| Starting cohort | 2,824 non-clinical records → 51 SNP clusters (10 mixed) |
| Final set (post-QC) | 64 genomes: 24 LMF, 40 non-LMF |
| Core replicons | IncFIB(S) 90.6%, IncFII(S) 89.1% — both reservoirs |
| Dominant backbone | AB461 in 58/64 genomes |
| Acquired AMR | 14/64 genomes; blaTEM-1 most common |
| Enriched in LMF after FDR | None (replicons, backbones, AMR, accessory genes) |

## Methods

- **Data**: NCBI Pathogen Detection (Dec 2025), non-clinical, serovar-confirmed Enteritidis. LMF defined by JEMRA a<sub>w</sub> ≤ 0.85 criterion.
- **QC**: QUAST (N50 ≥ 20 kb, ≤ 500 contigs, 4.4–5.0 Mb) + BUSCO ≥ 95% (enterobacterales_odb10).
- **Plasmids**: PlasmidFinder v2.1 (replicons) + MOB-suite (reconstruction/mobility).
- **Annotation**: Prokka v1.14.6 (plasmid genes) + AMRFinderPlus v4.2 (AMR).
- **Pangenome**: Panaroo v1.3.4 (99% core) + IQ-TREE v3.0.1 (phylogeny) + DIAMOND vs COG 2020.
- **Statistics**: Fisher exact + Cochran–Mantel–Haenszel by SNP cluster, Benjamini–Hochberg FDR (α = 0.05).

## Repository structure

```
metadata/              Curated cohort metadata (LMF and non-LMF)
data/processed/        Intermediate analysis tables
scripts/
  notebooks/           Analysis notebooks, numbered 01–14
  circos.R             Circular phylogeny visualization (R)
results/
  figures/             Publication figures
  tables/              Supplementary tables (Data S1–S11)
```

Assemblies are not stored here — retrieve from NCBI using accessions in `metadata/` and `results/tables/`.

## Reproduce

1. Start from `metadata/` for cohort and SNP cluster assignments.
2. Run `scripts/notebooks/` in order (01 → 14). Notebooks use tables in `data/processed/`.
3. Supplementary tables in `results/tables/` correspond to Data S1–S11 in the paper.

Tool versions matter — use the versions listed in Methods above.

## License

Code: [MIT](LICENSE). Data, tables, and figures: [CC BY 4.0](LICENSE-DATA.md).

## Contact

Kinley Tenzin · tenzin12@ksu.edu · Kansas State University
