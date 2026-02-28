# narrative-flow-analysis
An NLP research tool to quantify "Narrative Drift" between institutional news and public discourse. Uses TF-IDF, Cosine Similarity, and VADER sentiment analysis to visualize how topics like AI layoffs and nuclear power are reframed as they move from media to community platforms.

# Narrative Flow & Sentiment Divergence Analysis

An automated research tool designed to measure **Narrative Drift**—the structural and emotional disconnect between institutional news reporting and organic community discourse.

## Overview
This project uses Natural Language Processing (NLP) to track how specific high-variance topics (e.g., AI layoffs, Nuclear Energy, UBI) evolve as they move from establishment news cycles to public discussion on Reddit.

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
