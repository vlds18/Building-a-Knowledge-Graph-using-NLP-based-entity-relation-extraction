# PDF-Based Knowledge Graph Construction with spaCy, PyPDF2, and PyVis

This repository implements an end-to-end pipeline for extracting structured information from scientific PDF documents and converting it into a lightweight knowledge graph. The workflow performs PDF text extraction, sentence segmentation, rule-based entity and relation extraction, triplet construction, and interactive graph visualization.

## Project Overview

The main components of the pipeline are:

- PDF text extraction using PyPDF2
- Sentence segmentation using the spaCy English model
- Subject extraction using dependency labels containing "subj"
- Object extraction using dependency labels containing "obj"
- Relation extraction using spaCy's Matcher for verb-phrase patterns
- Triplet construction producing (subject, relation, object) triples
- Interactive knowledge graph visualization using PyVis
- Optional Google Drive integration inside Google Colab

## Dependencies

The notebook relies on the following Python libraries:

- PyPDF2
- spaCy
- tqdm
- pandas
- matplotlib
- pyvis
- IPython

## Installation

To install all dependencies, run:

```bash
pip install scispacy spacy tqdm pyvis PyPDF2
```

If needed, also install the spaCy model:

```bash
python -m spacy download en_core_web_sm
```
