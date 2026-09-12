# SE4095 Social Network Theory and Practice — Assignment 01
Political Blogosphere Network Analysis

## Folder structure

```
StudentID_SNTP_Assignment/
├── code/
│   ├── SNTP_Assignment_Analysis.ipynb   <- main notebook (run this)
│   ├── polblogs.gml                     <- input dataset (already included)
│   ├── figures/                         <- output figures (already generated; will be overwritten on re-run)
│   ├── tables/                          <- output CSV tables (already generated; will be overwritten on re-run)
│   └── data/                            <- preprocessing log + ranking comparison JSON
├── report/
│   └── report.pdf                       <- 5-page IEEE-format report
├── processed_data/
│   ├── polblogs_analysis_graph.graphml  <- cleaned 1222-node largest-weakly-connected-component graph
│   └── polblogs_full_cleaned.graphml    <- cleaned 1490-node graph (self-loops/duplicates removed, isolates kept)
└── README.md                            <- this file
```

All paths used inside the notebook are **relative to the `code/` folder**, so
the notebook can be run from that folder on any machine without editing any
paths.

## Dependencies

Python 3.10+ with:

- `networkx` >= 3.6
- `numpy`
- `pandas`
- `scipy`
- `matplotlib`

Install with:

```
pip install networkx numpy pandas scipy matplotlib jupyter nbconvert nbformat
```

## How to run

1. Open a terminal in the `code/` folder (the folder containing
   `SNTP_Assignment_Analysis.ipynb` and `polblogs.gml`).
2. Launch Jupyter and open the notebook:

   ```
   jupyter notebook SNTP_Assignment_Analysis.ipynb
   ```

   or, to reproduce the exact executed notebook non-interactively:

   ```
   jupyter nbconvert --to notebook --execute --inplace \
       SNTP_Assignment_Analysis.ipynb --ExecutePreprocessor.timeout=600
   ```

3. Run all cells top to bottom (`Kernel > Restart & Run All`). No manual
   steps or path edits are required. A full run takes under one minute.
4. Outputs are written to `code/figures/`, `code/tables/`, and `code/data/`
   as the notebook executes; the same tables and figures are already
   included in this submission from the last run.

## Dataset

`polblogs.gml` — Adamic, L. A., and Glance, N. (2005). *The Political
Blogosphere and the 2004 U.S. Election: Divided They Blog.* Proceedings of
the 3rd International Workshop on Link Discovery. Original source:
https://public.websites.umich.edu/~mejn/netdata/

The file is included as downloaded, with one header line added
(`multigraph 1`) so that NetworkX's GML reader can parse it as the directed
multigraph it actually is (see Part A of the notebook/report for why this
was necessary and how it was then cleaned into a simple graph).

## Random seeds

`SEED = 42` is set once at the top of the notebook (`random.seed`,
`np.random.seed`) and reused for the random-node-removal sample in Part C
and for all five Louvain community-detection seeds (`0, 1, 2, 3, 4`) in
Parts D/E.

## Before submitting

Replace the placeholder **"Student Name" / "Student ID"** on the title page
of `report/report.pdf` (edit `report/report.tex` and recompile with
`pdflatex report.tex` twice, or edit the PDF metadata directly) and rename
this folder and the final zip from `StudentID_SNTP_Assignment` to your
actual student ID before submission, per the assignment's naming
requirement (`StudentID_SNTP_Assignment.zip`).
