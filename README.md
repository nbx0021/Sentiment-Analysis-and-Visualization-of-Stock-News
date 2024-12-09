# Sentiment Analysis and Visualization of Stock News

This project aims to **extract stock news headlines**, perform **sentiment analysis**, and visualize the results to understand how news sentiment might impact stock market performance. The project uses **web scraping**, **NLP-based sentiment scoring**, and **data visualization** techniques.

---

## Table of Contents
1. [Overview](#overview)
2. [Tools and Libraries Used](#tools-and-libraries-used)
3. [Workflow](#workflow)
4. [Setup Instructions](#setup-instructions)
5. [Code Walkthrough](#code-walkthrough)
6. [Visualizations](#visualizations)
7. [Results](#results)
8. [Screenshots](#screenshots)
9. [Future Scope](#future-scope)
10. [Conclusion](#conclusion)

---

## Overview

The project scrapes news headlines for major stock tickers (e.g., AAPL, GOOG, MSFT) from the **Finviz** website, analyzes their sentiment using **NLTK's VADER**, and visualizes the sentiment trends.

---

## Tools and Libraries Used

- **Python**
- **BeautifulSoup**: For web scraping stock news.
- **Pandas**: For data manipulation and analysis.
- **NLTK (VADER)**: For sentiment analysis.
- **Matplotlib/Seaborn**: For visualizations.

---

## Workflow

The project follows these steps:

1. **Web Scraping**: Extract stock news headlines and timestamps from Finviz.
2. **Data Processing**: Parse and clean the news headlines into a structured format.
3. **Sentiment Analysis**: Use the **VADER** sentiment analyzer to compute sentiment scores.
4. **Visualization**: Plot sentiment scores and trends for different stock tickers.

---

## Setup Instructions

1. Clone the repository:
   ```bash
   git clone https://github.com/your_username/Sentiment-Analysis-and-Visualization-of-Stock News.git
   cd stock-sentiment-analysis
   ```

2. Install required libraries:
   ```bash
   pip install beautifulsoup4 pandas nltk matplotlib
   ```

3. Run the Jupyter Notebook:
   ```bash
   jupyter notebook
   ```

4. Open `Sentiment Analysis and Visualization of Stock News.ipynb` and execute all cells.

---

## Code Walkthrough

### 1. Web Scraping News Data
- The project uses **BeautifulSoup** to extract stock news headlines from Finviz.

```python
from urllib.request import Request, urlopen
from bs4 import BeautifulSoup

tickers = ['AAPL', 'GOOG', 'MSFT']
news_tables = {}

for ticker in tickers:
    url = f"https://finviz.com/quote.ashx?t={ticker}"
    req = Request(url, headers={'User-Agent': 'Mozilla/5.0'})
    response = urlopen(req)
    html = BeautifulSoup(response, 'html.parser')
    news_table = html.find(id="news-table")
    news_tables[ticker] = news_table
```

### 2. Parsing News Headlines
The extracted news is parsed to separate the **date**, **time**, and **title**.

### 3. Sentiment Analysis
The **VADER** SentimentIntensityAnalyzer assigns a **compound score** to each headline.

```python
from nltk.sentiment.vader import SentimentIntensityAnalyzer

vader = SentimentIntensityAnalyzer()
df['compound'] = df['title'].apply(lambda title: vader.polarity_scores(title)['compound'])
```

### 4. Visualization
Sentiment scores are visualized using **Matplotlib** to analyze trends over time.

---

## Visualizations

1. **Sentiment Distribution**: Shows the spread of positive, neutral, and negative sentiment.
2. **Sentiment Trend Over Time**: A line plot showing changes in sentiment for different stock tickers.

---

## Results

The analysis provides insights into:
- The sentiment polarity (positive/negative) of recent news headlines.
- How sentiment varies across stock tickers over time.

---

## Screenshots

### 1. **News Extraction Output**
![News Extraction](screenshots/news_extraction.png)

### 2. **Parsed DataFrame**
![Parsed DataFrame](screenshots/parsed_dataframe.png)

### 3. **Sentiment Scores**
![Sentiment Scores](screenshots/sentiment_scores.png)

### 4. **Visualization - Sentiment Trend**
![Sentiment Trend](screenshots/sentiment_trend.png)

---

## Future Scope

- Include stock price data to correlate sentiment with stock performance.
- Automate daily news scraping and analysis.
- Add more advanced NLP techniques like BERT for sentiment scoring.

---

## Conclusion

This project demonstrates how **news sentiment analysis** can provide valuable insights into stock market trends. By combining web scraping, sentiment analysis, and visualization, the project highlights the impact of news on stock sentiment.

