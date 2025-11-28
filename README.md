# 🕵️‍♂️ Literary Pattern Analyzer

This project implements an end-to-end **Natural Language Processing (NLP) pipeline** designed to analyze literary texts. Unlike standard datasets, this tool fetches raw corpus data directly from **Project Gutenberg** via HTTP requests, performs linguistic preprocessing using **NLTK**, and extracts statistical insights using **N-Gram analysis**.

The current implementation analyzes Sir Arthur Conan Doyle's *The Adventures of Sherlock Holmes* to uncover distinct writing patterns and word associations.

## 🚀 Key Features

*   **Direct Data Ingestion**: Fetches raw text streams programmatically using `requests`, eliminating the need for manual file downloads or CSV parsing.
*   **Robust Preprocessing**:
    *   **RegexpTokenizer**: Exact extraction of alphanumeric tokens without complex regex loops.
    *   **Porter Stemming**: Reduces words to their root forms (e.g., "running" $\to$ "run") for accurate frequency counting.
    *   **Noise Reduction**: Advanced filtering of stopwords and book-specific artifacts.
*   **N-Gram Extraction**: Analyzes Unigrams, Bigrams, and Trigrams to find common phrases using NLTK utilities.
*   **Advanced Visualization**: Uses **Seaborn** to generate high-quality, publication-ready statistical charts.

## 🛠️ Tech Stack

*   **Python 3.8+**
*   **Data Handling**: `pandas`, `requests`
*   **NLP**: `nltk` (Natural Language Toolkit)
*   **Visualization**: `seaborn`, `matplotlib`

## 📦 Installation

1.  Clone the repository:
    ```bash
    git clone https://github.com/kkk-6412/n-gram.git
    cd n-gram
    ```

2.  Install the required dependencies:
    ```bash
    pip install pandas seaborn matplotlib nltk requests
    ```

3.  Download necessary NLTK corpora (the script usually handles this, but to be safe):
    ```python
    import nltk
    nltk.download('stopwords')
    ```

## 📊 Methodology

The pipeline follows these distinct steps:

1.  **Ingestion**: The script sends a GET request to Project Gutenberg's servers to retrieve `1661-0.txt` (Sherlock Holmes).
2.  **Stream Processing**: The text is treated as a continuous stream rather than sentence-based rows. It is lowercased and tokenized using `RegexpTokenizer`.
3.  **Stemming**: Unlike simple lemmatization, this project uses the **PorterStemmer** algorithm to normalize word variations, making the analysis strictly distinct from standard academic tasks.
4.  **Analysis**: `nltk.util.ngrams` is used to build tuples of adjacent words.
5.  **Plotting**: Frequency distributions are converted to Pandas DataFrames and visualized using Seaborn's horizontal bar charts with distinct color palettes.

## 🖥️ Usage

Run the script directly in your Python environment or Jupyter Notebook (or Colab):

```python
# The script will output raw text samples, token counts, and display 3 charts.
python analysis_script.py
```

### Customization
To analyze a different book, simply change the `target_url` variable in the script:

```python
# Example: Dracula by Bram Stoker
target_url = "https://www.gutenberg.org/cache/epub/345/pg345.txt"
```

## 📈 Example Output

The tool generates visualizations for:
*   **Top 10 Words**: Highlighting key characters (e.g., *holmes*, *watson*).
*   **Bigrams**: Common pairs (e.g., *baker street*, *st clairs*).
*   **Trigrams**: Complex phrases (e.g., *mr sherlock holm*).

## 📄 License

This project is open-source and available under the MIT License. Data is sourced from [Project Gutenberg](https://www.gutenberg.org/), subject to their terms of use.
