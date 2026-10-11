# Raw Milk AMR Analysis

A culture-based microbiology and data-analysis portfolio project examining bacterial isolates from raw dairy milk, antibiotic susceptibility patterns, and reported farm-level hygiene practices in Nchiru, Meru County, Kenya.

> **Project status:** Initial portfolio scaffold. The uploaded analysis notebook is retained as an initial workflow, but it is **not yet a clean, end-to-end reproducible pipeline**: its code expects three Excel input files and worksheet names that do not match the datasets currently included here. The next step is to align the notebook to the actual files and validate every result against the source data before presenting findings as final.

## Research questions

1. Which bacterial groups were recorded in the milk samples?
2. What susceptibility patterns were recorded for the antibiotics tested?
3. Which reported hygiene practices are associated with the study's defined risk/contamination outcome, where the source data support that analysis?

## Repository layout

```text
raw-milk-amr-analysis/
├── data/
│   ├── raw/
│   │   └── hygiene_questionnaire.csv
│   └── processed/
│       └── cleaned_milk_data.xlsx
├── notebooks/
│   └── raw_milk_analysis_initial.ipynb
├── reports/
│   ├── interpreted_ast_results_reference.docx
│   └── statistical_analysis_report_reference.docx
├── .gitignore
├── README.md
└── requirements.txt
```

## Data and interpretation notes

- `data/raw/hygiene_questionnaire.csv` contains coded questionnaire responses. Use the accompanying codebook or study documentation to interpret numeric codes.
- `data/processed/cleaned_milk_data.xlsx` contains a cleaned study workbook with microbiology and questionnaire-related fields.
- The AST document contains interpreted susceptibility categories (`S`, `I`, `R`, and `NT`) for the listed isolates. It is a reference document, not a machine-readable analysis input.
- The statistical report is retained for comparison and review. Do not treat its figures as independently reproduced until the analysis has been rerun from the included source data.
- No participant names should be added to this repository. Check all files for personal or confidential information before making the repository public.

## Important scientific limitations

- A hygiene risk score is not the same as measured bacterial concentration (CFU/mL). Do not label a score-derived category as laboratory-confirmed contamination unless actual CFU/mL results support that claim.
- The study sample is small. Inferential statistics and any regression should be presented as exploratory, with uncertainty and sparse-cell limitations stated.
- Report antibiotic susceptibility using the applicable CLSI edition and organism–drug breakpoints. Do not infer multidrug resistance from a simple count of resistant results unless the antimicrobial classes and applicable definition have been verified.
- Keep `NT` (not tested) distinct from susceptible, intermediate, and resistant results; exclude `NT` from the tested denominator when calculating S/I/R percentages.
- Verify isolate identity, antibiotic disk contents, zone diameters, and interpretation criteria against laboratory records before making clinical or epidemiological claims.

## Setup

Python 3.10 or later is recommended.

```bash
python -m venv .venv
source .venv/bin/activate       # Linux/macOS
# Windows: .venv\\Scripts\\activate
pip install -r requirements.txt
jupyter lab
```

Open `notebooks/raw_milk_analysis_initial.ipynb`.

**Note:** The initial notebook currently refers to input files and sheet names not present in this repository, so it will need data-loading and schema updates before it runs from top to bottom. Do not claim the workflow is fully reproducible until that is fixed and tested.

## Suggested analysis workflow

1. Validate sample IDs and the number of unique samples.
2. Inspect missing values, duplicate records, and organism coding.
3. Produce descriptive bacterial-isolate summaries with clearly stated denominators.
4. Summarize AST categories by organism and antibiotic, keeping untested results separate.
5. Analyze hygiene responses using the codebook and a clearly defined outcome.
6. Use suitable tests for small categorical samples and report effect sizes/uncertainty where possible.
7. Export figures and tables with scripts or notebooks that can be rerun.

## Tools

Python, pandas, NumPy, SciPy, statsmodels, Matplotlib, Seaborn, Plotly, openpyxl, and Jupyter.

## Reproducibility checklist

- [ ] Align notebook inputs and worksheet names to files in this repository.
- [ ] Validate data types, sample identifiers, missing values, and duplicates.
- [ ] Verify AST interpretation criteria and antibiotic denominators.
- [ ] Re-run the complete notebook from a fresh kernel.
- [ ] Export final figures/tables and document exact methods.
- [ ] Remove private information and confirm permission to publish the data.
