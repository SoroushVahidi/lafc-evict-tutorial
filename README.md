# LAFC-Evict tutorial

This repository contains the "Get To Know A Dataset" tutorial notebook for
**LAFC-Evict: Learning-Augmented Cache Eviction Dataset**, prepared for the
[AWS Registry of Open Data](https://registry.opendata.aws/).

## What LAFC-Evict is

LAFC-Evict is a derived, tabular research dataset of counterfactual
supervision labels for learning-augmented cache-eviction research. Each row
describes one candidate object considered for eviction at one
full-cache-miss decision point, together with engineered state/candidate
features and a label describing what would happen to the cache miss rate
over a short future horizon if that specific candidate were evicted. It is
computed by the dataset author from third-party, CC0-1.0 Wikimedia pageview
data, and it does not redistribute any raw Wikimedia rows, page titles, or
other third-party trace data.

## Scope of this tutorial

This tutorial covers the current public release, **v0.3**:

- **22,356,992** candidate rows
- Built entirely from the **`wiki2018`** trace family (single source family — no other trace family is included)
- License: **CC0-1.0**

## The public data

The dataset is hosted on the AWS Open Data public S3 bucket:

- S3 URI: `s3://lafc-evict-open-data/`
- HTTPS base: `https://lafc-evict-open-data.s3.us-west-2.amazonaws.com/`

All objects are publicly readable with no AWS account or credentials
required (anonymous access). The same data is also available on
[Hugging Face](https://huggingface.co/datasets/SoroushVahidi/lafc-evict).

## The notebook

[`get-to-know-a-dataset.ipynb`](get-to-know-a-dataset.ipynb) walks through:

1. Loading a small, representative slice of LAFC-Evict without downloading the full file (via HTTP range reads against the public S3 bucket).
2. Inspecting the schema and the columns that matter for a candidate-eviction-prediction task.
3. A simple exploratory analysis (loss by cache capacity) and a visualization.
4. What the main `y_loss` / `y_value` label does and does not mean.
5. One worked research question this dataset already supports, and one open question it does not yet answer.

### Running it

The notebook only needs generic data-science packages — no AWS account or
credentials are required, since it reads the public bucket anonymously over
HTTPS:

```bash
pip install "pyarrow>=14" "fsspec>=2024.2" "pandas>=2.0" "matplotlib>=3.7"
jupyter notebook get-to-know-a-dataset.ipynb
```

## Further documentation

Full schema, provenance, and limitations documentation for the dataset is
maintained on its Hugging Face dataset card:
<https://huggingface.co/datasets/SoroushVahidi/lafc-evict>

## Generator source

The cache simulator and candidate-row feature/label generation pipeline
that produced this dataset is public:
<https://github.com/SoroushVahidi/Augmented-caching> (branch `main`).

## Citation

```bibtex
@dataset{vahidi_lafc_evict_v0_3,
  author    = {Vahidi, Soroush},
  title     = {LAFC-Evict: Learning-Augmented Cache Eviction Dataset (v0.3)},
  year      = {2026},
  publisher = {Hugging Face},
  url       = {https://huggingface.co/datasets/SoroushVahidi/lafc-evict}
}
```

## License

See [`LICENSE`](LICENSE). The dataset itself is CC0-1.0; this tutorial's
materials (notebook and documentation in this repository) are also
dedicated to the public domain under CC0-1.0, to match the dataset's own
licensing and keep reuse simple.

## Contact

sv96@njit.edu
