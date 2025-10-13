# Roget's Thesaurus Scraper

This repository contains a Python script within a Jupyter Notebook that scrapes, parses, and structures the content of *Roget's Thesaurus* from the Project Gutenberg website. The script organizes the complex structure of the thesaurus into a hierarchical JSON file.

## How It Works

The script performs the following steps:

1.  **Fetch Data**: It sends an HTTP GET request to the Project Gutenberg URL for Roget's Thesaurus (`https://www.gutenberg.org/cache/epub/22/pg22-images.html`).
2.  **Parse HTML**: Using the `BeautifulSoup` library, it parses the downloaded HTML content.
3.  **Identify Hierarchy**: The script iterates through the HTML tags (`h2`, `h3`, `h4`, `h5`) to reconstruct the thesaurus's classification system, starting from "CLASS I".
4.  **Extract & Clean**:
    - Custom functions `extract_word` and `extract_synonyms` are used to pull headwords and their corresponding synonyms from paragraph tags.
    - The data is cleaned to remove unwanted characters, annotations (e.g., `[... ]`, `{...}`), part-of-speech markers (e.g., `N.`, `V.`, `adj.`), and formatting inconsistencies.
5.  **Structure Data**: The cleaned data is assembled into a nested dictionary that mirrors the original structure of the thesaurus.
6.  **Save Output**: The final hierarchical dictionary is saved as a JSON file.

## Output

After running the script, a file named `rogets_thesaurus_hierarchy.json` will be created in the root directory. This file contains the full thesaurus, structured as a nested JSON object.

### Example JSON Structure:

```json
{
    "CLASS IWORDS EXPRESSING ABSTRACT RELATIONS": {
        "SECTION I. EXISTENCE": {
            "1. ABSTRACT": {
                "Existence": [
                    "reality",
                    "actuality",
                    "positive existence",
                    "fact",
                    "matter of fact",
                    "stubborn fact",
                    "scire facias"
                ],
                "Inexistence": [
                    "nonexistence",
                    "nonentity",
                    "negative existence",
                    "nullity",
                    "nihility",
                    "nihilism",
                    "nolition",
                    "vacuity",
                    "tabula rasa",
                    "blank",
                    "abeyance",
                    "absence",
                    "absentee",
                    "no one",
                    "nobody",
                    "Nemo",
                    "negation"
                ]
            }
        }
    }
}
```

## Requirements

- Python 3.x
- `requests`
- `beautifulsoup4`

## Usage

1.  Clone the repository to your local machine:
    ```sh
    git clone https://github.com/kosmaskanellakis/assignment-3_rogets_thesaurus.git
    cd assignment-3_rogets_thesaurus
    ```

2.  Install the necessary dependencies:
    ```sh
    pip install requests beautifulsoup4
    ```

3.  Run the cells in the Jupyter Notebook `Assignment3_rogets_thesaurus.ipynb`.

4.  Upon completion, the `rogets_thesaurus_hierarchy.json` file will be generated in the project directory.
