# PDF-based Knowledge Graph Construction with spaCy, PyPDF2, and PyVis

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
## Pipeline structure

### 1. PDF text extraction
The pipeline reads the PDF file page-by-page and extracts text using PyPDF2's PdfReader.

### 2. Sentence tokenization
The extracted text is processed with spaCy to identify sentence boundaries.

### 3. Entity extraction (Subject and Object)
Dependency parsing is applied to detect:

- Subjects through dependency labels containing "subj"
- Objects through dependency labels containing "obj"

Compound and modifier tokens are merged to form complete entity names.

### 4. Relation extraction
spaCy's Matcher identifies the root verb and optional modifiers (prepositions, agents, adjectives) to extract verb-phrase relations.

### 5. Triplet assembly
Each sentence yields a candidate triple:

```bash
(subject, relation, object)
```

These are stored in a pandas DataFrame after filtering incomplete entries.

### 6. Knowledge Graph visualization
Triples are rendered as an interactive network using PyVis.
The output is saved as:

```bash
kg.html
```

This file can be opened in any browser and supports zooming, node selection, and tooltips.

## Output

- An HTML knowledge graph visualization
- A DataFrame of extracted (subject, relation, object) triples

## Use cases

- Biomedical literature mining
- Genomics and cancer research
- Domain-specific knowledge graph construction
- Pre-processing for ontology alignment or downstream RAG systems

