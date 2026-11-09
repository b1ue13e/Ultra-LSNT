# Ultra-LSNT

[中文说明](README.zh-CN.md) · [Repository](https://github.com/b1ue13e/Ultra-LSNT)

Public reproducibility repository for the manuscript:

> "Controller-side feasibility guidance for wind power forecasting under corrupted SCADA"

Ultra-LSNT is the model family and experiment codebase behind the paper's controller-side forecasting study under corrupted SCADA conditions. The repository is organized for paper-aligned reproducibility rather than as a polished software package.

## At a glance

- Main model: Ultra-LSNT and Ultra-LSNT-Lite
- Main task: controller-side wind power forecasting under corrupted SCADA
- Public assets: code, released Wind (CN) data assets, processed benchmark datasets, split manifests, figures, and result tables
- License: MIT

## Start here

- `QUICKSTART.md` for the fastest local setup
- `DATA.md` for released datasets and split manifests
- `EXPERIMENTS.md` for the main experiment scripts
- `STRUCTURE.md` for a repository map
- `docs/README.md` for archived reports and maintainer notes
- `CONTRIBUTING.md` for contribution and issue-reporting guidance
- `CITATION.cff` for machine-readable citation metadata

## What is in this repository

- Ultra-LSNT model implementations
- Baseline comparison scripts
- Corrupted-SCADA robustness evaluation
- Batch-1 efficiency benchmarking
- Ablation and feasibility-oriented experiments
- Cross-domain diagnostic experiments
- Public reproducibility assets referenced by the paper

## Repository layout

```text
Ultra-LSNT/
|- src/                          Models, baselines, experiments, utilities
|- scripts/                      Batch helper scripts
|- data/
|  |- raw/                       Raw Wind (CN) release
|  `- processed/                 Processed data tables
|- results/
|  |- figures/                   Paper-facing figures
|  `- tables/                    Reported and supporting result tables
|- docs/                         Archive and maintainer-facing notes
|- split_manifest_80_20.json
|- split_manifest_80_20_unified.json
`- root-level compatibility CSV files for older scripts
```

The canonical data location is `data/`. Root-level CSV copies are intentionally retained only to preserve compatibility with older scripts that expect those filenames in the repository root.

## Verification and documentation

- [Quick start](QUICKSTART.md): environment setup and fastest readable sanity check.
- [Data guide](DATA.md): canonical paths for raw Wind (CN), processed datasets, and root compatibility CSVs.
- [Experiments guide](EXPERIMENTS.md): primary scripts for training, robustness, efficiency, ablation, and cross-domain diagnostics.
- [Structure](STRUCTURE.md) and [Summary](SUMMARY.md): repository layout and project scope.
- [Documentation archive](docs/README.md): historical reports in `docs/archive/` and maintainer notes in `docs/maintainers/`.
- [License](LICENSE) and [Contributing](CONTRIBUTING.md): terms and issue-reporting conventions.

This repository contains published code and benchmark assets for paper inspection; it is not a packaged library and does not include unverified automated performance guarantees.

## Data availability

### Main Wind (CN) assets

- Raw time series: `data/raw/wind_main.csv`
- Processed tables:
  - `data/processed/wind_final.csv`
  - `data/processed/processed_wind.csv`
- Chronological split manifests:
  - `split_manifest_80_20.json`
  - `split_manifest_80_20_unified.json`
- Preprocessing entry point: `src/data_preprocess.py`

### Secondary diagnostic datasets

- `data/processed/wind_us.csv`
- `data/processed/air_quality_ready.csv`
- `data/processed/gefcom_ready.csv`

## Quick setup

```bash
git clone https://github.com/b1ue13e/Ultra-LSNT.git
cd Ultra-LSNT
pip install -r requirements.txt
python src/experiments/run_multi_domain_baselines.py --help
```

If the last command prints the argument list, the public repository layout is working as intended.

## Main entry points

```bash
# Main Wind (CN) training
python src/experiments/train_ultra_lsnt_stable.py

# Corrupted-SCADA robustness
python src/experiments/run_universal_robustness.py

# Efficiency benchmark
python src/experiments/run_efficiency_benchmark.py

# Ablation study
python src/experiments/run_comprehensive_ablation.py

# Cross-domain diagnostics
python src/experiments/run_multi_domain_baselines.py
```

## Reproducibility notes

- The released evaluation protocol follows chronological 80/20 splitting.
- Split definitions used in the paper are included directly in the checked-in manifest files.
- Several scripts were developed during manuscript preparation and still expect root-level filenames such as `wind_final.csv`; compatibility copies are retained for that reason.
- The repository is intended to support inspection and reruns of the paper's workflows, not to claim production-grade deployment readiness.

## Citation

If you use this repository, the released data assets, or the corrupted-SCADA evaluation workflow, please cite:

```bibtex
@article{li2026ultralsnt,
  title   = {Controller-side feasibility guidance for wind power forecasting under corrupted SCADA},
  author  = {Li, Junyu and Du, Juntao},
  journal = {Applied Energy},
  year    = {2026},
  note    = {Under review}
}
```

## License

This project is released under the MIT License. See `LICENSE` for details.
