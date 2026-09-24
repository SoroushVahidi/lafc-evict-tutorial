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
over a short future horizon if that specific candidate were evicted. v1.0
is derived from five cleared trace families and does not redistribute raw
upstream traces, raw Wikimedia rows, raw page titles, or other third-party
raw data.

## Scope of this tutorial

This tutorial covers the current AWS public release, **v1.0**:

- **277,995,072** candidate rows
- **2,363,286** decision-view rows
- **1,000,000** pairwise-sample rows
- Five included families: `cloudphysics`, `metacdn`, `metakv`, `twemcache`, `wiki2018`
- Excluded families: `citibike`, `brightkite`
- License: **CC0-1.0**

The historical v0.3 AWS release remains available at the bucket root for
reproducibility.

## The public data

The dataset is hosted on the AWS Open Data public S3 bucket:

- Current S3 URI: `s3://lafc-evict-open-data/v1.0/`
- Current HTTPS base: `https://lafc-evict-open-data.s3.us-west-2.amazonaws.com/v1.0/`
- Historical v0.3 S3 URI: `s3://lafc-evict-open-data/`

All objects are publicly readable with no AWS account or credentials
required (anonymous access). The same data is also available on
[Hugging Face](https://huggingface.co/datasets/SoroushVahidi/lafc-evict).

## The notebook

[`get-to-know-a-dataset.ipynb`](get-to-know-a-dataset.ipynb) walks through:

1. Loading the v1.0 release manifest without credentials.
2. Reading one small candidate-row Parquet object from public S3.
3. Inspecting schema and basic label/feature columns.
4. Understanding the decision and pairwise views without downloading the full ~3 GB release.
5. Reviewing scope, excluded families, provenance, and checksum guidance.

### Running it

The notebook only needs generic data-science packages — no AWS account or
credentials are required, since it reads the public bucket anonymously over
HTTPS:

```bash
pip install "pyarrow>=14" "pandas>=2.0"
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
@dataset{vahidi_lafc_evict_v1_0,
  author    = {Vahidi, Soroush},
  title     = {LAFC-Evict: Learning-Augmented Cache Eviction Dataset (v1.0)},
  year      = {2026},
  version   = {1.0},
  publisher = {AWS Open Data},
  url       = {s3://lafc-evict-open-data/v1.0/}
}
```

## License

See [`LICENSE`](LICENSE). The dataset itself is CC0-1.0; this tutorial's
materials (notebook and documentation in this repository) are also
dedicated to the public domain under CC0-1.0, to match the dataset's own
licensing and keep reuse simple.

## Contact

sv96@njit.edu
