# narrative-flow-analysis
An NLP research tool to quantify "Narrative Drift" between institutional news and public discourse. Uses TF-IDF, Cosine Similarity, and VADER sentiment analysis to visualize how topics like AI layoffs and nuclear power are reframed as they move from media to community platforms.

# Narrative Flow & Sentiment Divergence Analysis

An automated research tool designed to measure **Narrative Drift**—the structural and emotional disconnect between institutional news reporting and organic community discourse.

## Overview
This project uses Natural Language Processing (NLP) to track how specific high-variance topics (e.g., AI layoffs, Nuclear Energy, UBI) evolve as they move from establishment news cycles to public discussion on Reddit.
## Methodology

The core of this analyzer relies on two Natural Language Processing (NLP) frameworks to quantify how information changes as it moves from institutional news to public discourse.

### 1. Linguistic Alignment (TF-IDF & Cosine Similarity)
To measure Narrative Drift, we represent each dataset (News and Reddit) as high-dimensional vectors. 

* **TF-IDF (Term Frequency-Inverse Document Frequency):** Instead of simple word counts, we use TF-IDF to weight words. This rewards words that are unique and descriptive of a specific topic (e.g., "thorium" in Nuclear Energy) while penalizing common "grammar noise" (e.g., "the", "and").
* **Cosine Similarity:** We calculate the cosine of the angle between the News vector ($A$) and the Reddit vector ($B$).
    $$\text{similarity} = \cos(\theta) = \frac{\mathbf{A} \cdot \mathbf{B}}{\|\mathbf{A}\| \|\mathbf{B}\|}$$
    * **Score of 1.0:** The narratives are perfectly synced (using the same vocabulary).
    * **Score < 0.3:** Significant "Narrative Drift"—the public is discussing an entirely different aspect of the story than the media.

### 2. Sentiment Profiling (VADER)
We use the **VADER** (Valence Aware Dictionary and sEntiment Reasoning) model, which is specifically tuned for the nuances of social media.

* **Heuristic-Based Analysis:** Unlike standard models, VADER understands **Intensity** (using ALL CAPS), **Punctuation** (!!!), and **Conjunctions** (e.g., the "but" shift, where "The tech is good, but the cost is high" results in a negative lean).
* **The Compound Score:** We aggregate individual comment scores into a normalized value between **-1 (Extreme Negative)** and **+1 (Extreme Positive)**. The "Sentiment Gap" in our charts represents the absolute difference between these two averages.

### 3. Topic Modeling (LDA)
For theme discovery, we apply **Latent Dirchlet Allocation (LDA)**. This is a generative statistical model that treats each platform as a "mixture of topics." By extracting the top 5 keywords per platform, we can visually identify if the News is focused on *Economic Actors* (CEOs, Profits) while Reddit is focused on *Social Impact* (Jobs, Ethics).

### Key Research Findings
* **Grassroots Optimism:** Identified cases where community discourse is significantly more positive than news reporting, despite discussing different sub-themes.
* **Narrative Silos:** Quantified topics where the "Linguistic Sync" (Cosine Similarity) is below 0.20, indicating a total disconnect between media framing and public concern.

## Features
* **Multi-Platform Scraping:** Simultaneous extraction from Google News (RSS) and Reddit (Pushshift/PullPush API).
* **Sentiment Profiling:** Comparative VADER sentiment analysis to identify "emotional gaps."
* **Linguistic Alignment:** Uses TF-IDF and Cosine Similarity to measure how much the two platforms talk past each other.
* **Theme Discovery:** Latent Dirichlet Allocation (LDA) to extract dominant topics from both datasets.
* **Visual Dashboard:** Automated side-by-side Matplotlib/Seaborn visualizations of sentiment and cleaned vocabulary.

## Sample Visualizations
<img width="1484" height="484" alt="image" src="https://github.com/user-attachments/assets/8d3266d0-3b89-4e16-a7e9-7dff63c7b79f" />

> **Topic: AI Related Layoffs**
> * News Focus: Profitability, Efficiency, Stock Price
> * Reddit Focus: Corporate Greed, job hunting, layoffs

## Get Started here

### Prerequisites
```bash
pip install spacy feedparser pandas matplotlib seaborn nltk scikit-learn
python -m spacy download en_core_web_sm
