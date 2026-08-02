# 🔍 Mini Search Engine (Information Retrieval System)

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-Web%20API-000000?style=for-the-badge&logo=flask&logoColor=white)
![Algorithms](https://img.shields.io/badge/Algorithms-Inverted%20Index%20%7C%20TF--IDF%20%7C%20BM25-brightgreen?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-purple?style=for-the-badge)

A high-performance, modular **Mini Search Engine** built from scratch in Python, featuring core Information Retrieval (IR) data structures and algorithms. Includes an inverted indexing pipeline, dual relevance ranking models (TF-IDF & Okapi BM25), spell correction using Levenshtein distance dynamic programming, a sleek glassmorphic Web UI, and an interactive CLI.

---

## 🌟 Key Features

- ⚡ **Inverted Index Data Structure**: Fast $O(1)$ dictionary-based term lookup mapping words to posting lists with term frequencies and exact token positions.
- 🔤 **Text Preprocessing Pipeline**: Tokenization, lowercasing, regex filtering, stop-word removal, and rule-based stemming.
- 📊 **Dual Ranking Algorithms**:
  - **TF-IDF (Term Frequency - Inverse Document Frequency)** with cosine normalization.
  - **Okapi BM25** probabilistic relevance model with document length normalization parameters ($k_1=1.5, b=0.75$).
- 💡 **Dynamic Programming Spell Checker**: Calculates Levenshtein minimum edit distance to generate automatic *"Did you mean?"* query suggestions.
- 🎨 **Glassmorphism Web UI**: Sleek dark-mode interface built with HTML5, CSS3, and JavaScript featuring real-time autocomplete, term highlighting, and live metrics.
- ➕ **Dynamic Indexing**: Allows users to index custom text documents dynamically via Web UI modal or REST API.
- 🖥️ **Interactive Terminal CLI**: Lightweight command-line interface for searching and toggling ranking algorithms directly in the terminal.
- 🧪 **Unit Test Suite**: Full test coverage using Python `unittest` / `pytest`.

---

## 🧮 Mathematical Foundations

### 1. Inverted Index Mapping
Given a corpus of $N$ documents, the inverted index maps term $t$ to postings:
$$\text{Index}(t) \to \{ d_i : (\text{TF}(t, d_i), [\text{pos}_1, \text{pos}_2, \dots]) \}$$

### 2. TF-IDF Weighting
$$\text{TF}(t, d) = \frac{f(t, d)}{|d|}$$
$$\text{IDF}(t) = \ln\left( \frac{N + 1}{\text{DF}(t) + 1} \right) + 1$$
$$\text{Score}(Q, d) = \sum_{t \in Q} \text{TF}(t, d) \times \text{IDF}(t)$$

### 3. Okapi BM25 Relevance Score
$$\text{Score}_{\text{BM25}}(D, Q) = \sum_{i=1}^{n} \text{IDF}(q_i) \cdot \frac{f(q_i, D) \cdot (k_1 + 1)}{f(q_i, D) + k_1 \cdot \left(1 - b + b \cdot \frac{|D|}{\text{avgdl}}\right)}$$

---

## 🏗️ Project Architecture

```
mini-search-engine/
├── search_engine/
│   ├── __init__.py        # Package initialization
│   ├── tokenizer.py       # Regex tokenization, stop-words, simple stemming
│   ├── inverted_index.py  # Inverted index posting list & metadata storage
│   ├── ranker.py          # TF-IDF & Okapi BM25 scoring implementations
│   ├── spell_check.py     # Levenshtein DP edit distance spell checker
│   ├── corpus.py          # Pre-populated CS/Tech document corpus
│   └── engine.py          # Main façade orchestrating search pipeline
├── templates/
│   └── index.html         # Web search page template
├── static/
│   ├── css/style.css      # Glassmorphism dark mode stylesheet
│   └── js/app.js          # Interactive frontend logic & async REST queries
├── tests/
│   └── test_engine.py     # Automated unit test suite
├── app.py                 # Flask REST API server
├── cli.py                 # Command line interactive search interface
├── requirements.txt       # Project dependencies
├── .gitignore             # Git ignore patterns
└── README.md              # Project documentation
```

---

## 🚀 Quick Start Guide

### Prerequisites
- Python 3.8 or higher installed on your machine.

### 1. Clone & Set Up Project
```bash
# Clone the repository (or open directory in VS / VS Code)
cd mini-search-engine

# Create virtual environment (optional but recommended)
python -m venv venv
# Windows activate:
venv\Scripts\activate
# Mac/Linux activate:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

### 2. Run the Web Application
```bash
python app.py
```
Open your browser and navigate to **`http://127.0.0.1:5000`**.

### 3. Run the Terminal CLI
```bash
python cli.py
```

### 4. Run Unit Tests
```bash
python -m unittest discover tests
# or using pytest:
pytest
```

---

## 🐙 How to Upload to Your GitHub Profile

Follow these simple steps in VS Code Terminal or Command Prompt:

```bash
# 1. Initialize git repository
git init

# 2. Add all project files
git add .

# 3. Commit your code
git commit -m "Initial commit: Mini Search Engine IR system with Flask UI"

# 4. Create a new repository on GitHub (https://github.com/new), then run:
git branch -M main
git remote add origin https://github.com/YOUR_GITHUB_USERNAME/mini-search-engine.git
git push -u origin main
```

---

## 📄 License
This project is open-source and available under the [MIT License](LICENSE).
