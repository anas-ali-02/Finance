# Algorithmic Trading with Unsupervised Learning

This project, outlined in a Jupyter Notebook, demonstrates the development of an algorithmic trading strategy using unsupervised machine learning. The core idea is to group similar stocks using clustering and then build a portfolio from a selected cluster.

## Table of Contents
1.  [Project Idea](#project-idea)
2.  [Key Concepts](#key-concepts)
3.  [Project Workflow](#project-workflow)
4.  [Visualizations](#visualizations)

---

## 1. Project Idea

The primary goal of this project is to create a data-driven trading strategy. Instead of relying on a pre-defined model, the approach uses **unsupervised learning** to identify natural groupings of stocks based on their statistical and technical characteristics. By identifying these clusters, we can then select a group of stocks that exhibit similar behaviors and construct a portfolio from that group. The portfolio's performance is then optimized for the highest possible risk-adjusted return.

---

## 2. Key Concepts

### Algorithmic Trading
The use of computer programs and algorithms to automatically execute trades in the financial markets. This project automates the process of data analysis, stock selection, and portfolio optimization.

### Unsupervised Learning
A type of machine learning where the algorithm is not given labeled data. It is tasked with finding patterns and structures within the data on its own. In this project, we use **K-Means Clustering** to identify and group similar stocks.

### Fama-French Factors
A set of factors widely used in finance to explain asset returns. The project uses the 5-factor model, which includes:
* **Market Risk:** The risk associated with the overall market.
* **Size:** The size of a company (small-cap vs. large-cap).
* **Value:** A company's book-to-market ratio (value stocks vs. growth stocks).
* **Operating Profitability:** A measure of a company's profit margin.
* **Investment:** How much a company invests in its assets.

These factors provide a deeper understanding of a stock's risk and return characteristics beyond simple price movements.

---

## 3. Project Workflow

The project is structured into several key steps:

#### **Step 1: Data Acquisition**
* The code downloads a list of **S&P 500** companies from Wikipedia.
* It then uses the `yfinance` library to download historical stock price data for these companies over eight years.

#### **Step 2: Feature Engineering**
* **Technical Indicators:** The notebook calculates several technical indicators using the `pandas_ta` library, including **Garman-Klass Volatility**, **RSI**, **Bollinger Bands**, **ATR**, and **MACD**.
* **Monthly Returns:** The code calculates monthly returns for various time horizons (1, 2, 3, 6, 9, 12 months) to capture momentum.
* **Fama-French Betas:** The project uses a rolling linear regression (`RollingOLS`) to estimate each stock's exposure (betas) to the 5 Fama-French factors.

#### **Step 3: Data Processing and Filtering**
* The daily data is aggregated into a **month-end frequency**.
* Stocks are filtered to include only the top 150 most liquid stocks each month based on their dollar volume.

#### **Step 4: K-Means Clustering**
* At the end of each month, the **K-Means Clustering** algorithm is applied to the data. This group's stocks are clustered into a predefined number of clusters based on their calculated features.

#### **Step 5: Portfolio Construction**
* A portfolio is constructed by selecting all the stocks within a chosen cluster.
* The portfolio weights are then optimized using the **Efficient Frontier** method, to maximize the **Sharpe ratio** (a measure of risk-adjusted return).

---

## 4. Visualizations

The final output of the project includes visualizations that compare the performance of the machine learning-driven portfolio against a benchmark, such as the **S&P 500 index**. This allows for a clear evaluation of the strategy's effectiveness.
