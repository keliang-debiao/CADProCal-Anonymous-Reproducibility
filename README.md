CADProCal Reproducibility Package

This repository contains the supporting materials for the CADProCal study on cross-dataset mathematical misconception retrieval. The package is organized for reference-table verification, summary-statistic recomputation, figure reconstruction, report generation, and automated testing.

Repository Contents

CADProCal_relaxed_reproduction/
├── CADProCal_Submission_Ready_Manuscript.docx
├── README.md
├── requirements-relaxed.txt
├── reference_targets/
│   ├── ablation.csv
│   ├── baseline_cv.csv
│   ├── calibration.csv
│   ├── efficiency.csv
│   ├── external_validation.csv
│   ├── internal_cv.csv
│   ├── interpretability.csv
│   ├── robustness.csv
│   └── statistics.csv
├── scripts/
│   ├── extract_manuscript.py
│   ├── reproduce_relaxed.py
│   └── run_relaxed.ps1
├── tests/
│   └── test_relaxed_reproduction.py
└── outputs/
    └── relaxed_reproduction/
        ├── comparison.csv
        ├── RELAXED_REPRODUCTION_REPORT.md
        ├── reproduction_summary.json
        ├── metrics/
        └── figures/

Manuscript File

CADProCal_Submission_Ready_Manuscript.docx contains the manuscript associated with the package and provides the source context for the reference tables and reconstructed figures.

Reference Tables

The reference_targets/ directory contains machine-readable CSV files organized by analysis type:

internal_cv.csv: fold-level internal cross-validation entries.

baseline_cv.csv: fold-level baseline and proposed-method entries.

external_validation.csv: external-validation entries.

ablation.csv: component-ablation entries.

calibration.csv: probability-calibration and prediction-set entries.

robustness.csv: perturbation and overlap-audit entries.

statistics.csv: statistical-comparison entries.

efficiency.csv: parameter, computation, and latency entries.

interpretability.csv: grouped interpretability entries.

Scripts

scripts/reproduce_relaxed.py

The main Python script loads the reference CSV files, recomputes the configured summary statistics, compares reconstructed values with the stored targets, generates the figure files, records file hashes, and writes machine-readable and human-readable output summaries.

scripts/run_relaxed.ps1

This PowerShell wrapper uses uv to create an isolated Python 3.11 environment, installs the dependencies listed in requirements-relaxed.txt, runs the main reproduction script, and executes the automated test suite.

scripts/extract_manuscript.py

This auxiliary script extracts paragraph and table text from a DOCX manuscript. It can print the full document structure or restrict the output to tables. The script uses the python-docx package and is separate from the main reproduction workflow.

Automated Tests

tests/test_relaxed_reproduction.py contains checks for:

the presence of all expected reference CSV files;

successful completion of the configured numerical checks; and

generation of all configured figure files.

Generated Outputs

The outputs/relaxed_reproduction/ directory contains:

comparison.csv, which stores the target-versus-reconstructed comparison records;

RELAXED_REPRODUCTION_REPORT.md, which provides a Markdown execution report;

reproduction_summary.json, which provides a structured execution summary;

metrics/, which contains copies of the processed metric tables; and

figures/, which contains the reconstructed figure files.

Main Dependencies

The main workflow uses:

Python 3.11

NumPy

pandas

Matplotlib

pytest

uv for isolated execution through the supplied PowerShell wrapper

The optional manuscript-extraction utility additionally requires python-docx.

Package Scope

The repository contains the manuscript, structured reference tables, verification and visualization scripts, generated outputs, and automated tests. It does not include the original datasets, model checkpoints, per-sample prediction files, or a full model-training pipeline.
