

# 📈 Web3 Trading Behavior vs. Market Sentiment Analysis

## 🎯 Project Objective

This project analyzes how trader behavior in the Bitcoin market changes with market sentiment, specifically comparing Fear and Greed periods. The goal is to understand how profitability, risk, trading volume, and aggressiveness differ between these sentiments, and to uncover actionable insights for trading strategies.

We use historical trade data and the Fear & Greed Index (FGI) to drive the analysis.

-----

## 📁 Submission Structure

This repository follows the required submission format:

```
ds_<candidate_name>/  (Your root directory)
├── notebook1.ipynb    (Main analysis notebook)
├── csv_files/
│   ├── fear_greed_index.csv
│   └── historical_data.csv
├── outputs/
│   ├── 01_avg_pnl_by_sentiment.png
│   ├── 02_volatility_by_sentiment.png
│   ├── 03_leverage_proxy_by_sentiment.png
│   ├── 04_win_rate_by_sentiment.png
│   ├── 05_buy_vs_sell_skew.png
│   ├── 06_pnl_vs_fgi.png
│   └── 07_clusters_volume_pnl.png
├── executive_summary.txt  (Generated summary of findings)
├── ds_report.pdf      (Detailed report)
└── README.md          (This file)
```

**Note:** The notebook generates the executive summary and saves it as `executive_summary.txt`.

-----

## 🛠️ Setup and Execution Instructions

The analysis is designed to run entirely within a **Google Colab environment** for ease of use, as it handles dependencies and provides GPU support if needed. It can also be run locally with Jupyter Notebook or JupyterLab, provided the dependencies are installed.

### Prerequisites

1.  **Environment:**
    - **Recommended:** Google Colab (free, cloud-based, no local setup required).
    - **Alternative:** Local Python environment with Jupyter Notebook/JupyterLab (Python 3.7+ recommended).

2.  **GitHub:** Clone this repository locally or directly open the notebook in Colab via GitHub integration.

3.  **Data Access:** The notebook downloads datasets from Google Drive links embedded in the code. Ensure internet access for downloads. If running locally, the links must be publicly accessible or you may need to adjust to local file paths.

### Dependencies

The notebook requires the following Python libraries (install via `pip` if running locally):

- `gdown` (for downloading files from Google Drive)
- `pandas` (data manipulation)
- `numpy` (numerical computations)
- `matplotlib` (plotting)
- `seaborn` (statistical visualizations)
- `scipy` (statistical tests)
- `statsmodels` (time series modeling, e.g., ARIMA)
- `scikit-learn` (machine learning models, e.g., Random Forest, KMeans)

In Google Colab, most libraries (except `gdown`) are pre-installed. Install `gdown` as shown in the notebook.

### Step-by-Step Instructions

1.  **Open the Notebook:**
    - In Google Colab: Go to [colab.research.google.com](https://colab.research.google.com), select "File" > "Open notebook" > "GitHub", and paste the repository URL to open `notebook1.ipynb`.
    - Or [Click here](https://colab.research.google.com/drive/1N-4btCLDdJWacYbadR1VrhezswlrGXEO?usp=sharing) to open `notebook1.ipynb` directly. 
    - Locally: Open `notebook1.ipynb` in Jupyter Notebook/JupyterLab after cloning the repo.

2.  **Install Dependencies (if needed):**
    - Run the first code cell in the notebook to install `gdown`:
      ```python
      !pip install -q gdown
      ```
    - If running locally and missing other libraries, install them via:
      ```bash
      pip install pandas numpy matplotlib seaborn scipy statsmodels scikit-learn gdown
      ```

3.  **Download Datasets:**
    - Run the "Downloading the datasets" section. This cell:
      - Creates the `csv_files` folder if it doesn't exist.
      - Downloads `fear_greed_index.csv` and `historical_data.csv` from the provided Google Drive links.
      - Extracts file IDs from the links and saves files to `csv_files/`.
    - **Note:** This step is mandatory as the rest of the notebook depends on these files. If downloads fail, verify link accessibility or upload files manually to `csv_files/`.

4.  **Configure Environment:**
    - Run the "Configuration and setup" cell to:
      - Suppress warnings.
      - Set Seaborn theme to "whitegrid" with "viridis" palette.
      - Create the `outputs` folder for saving plots.

5.  **Execute the Analysis:**
    - Run all cells sequentially or use **"Runtime" > "Run all"** in Colab.
    - The notebook is structured into sections:
      - **I. Data Loading & Cleaning:** Loads and cleans sentiment and trade data.
      - **II. Feature Engineering:** Creates daily metrics like PnL, volume, win rate, etc.
      - **III. Merge Datasets:** Aligns sentiment with trading behavior.
      - **IV. Statistical & ML Modeling:** Performs ARIMA, Random Forest, KMeans, and T-test.
      - **V. Visualization:** Generates and saves 7 plots to `outputs/`.
      - **VI. Executive Summary:** Computes insights and saves to `executive_summary.txt`.

6.  **View Outputs:**
    - Plots are displayed inline in the notebook and saved as `.png` files in `outputs/`.
    - The executive summary is printed and saved to `executive_summary.txt`.
    - If models fail (e.g., due to insufficient data), the notebook handles errors gracefully and provides fallback messages.

### Troubleshooting

- **Download Issues:** If `gdown` fails, check Google Drive link permissions or download manually and place in `csv_files/`.
- **Library Errors:** Ensure Python version is 3.7+. Update pip and reinstall packages if needed.
- **Colab Timeouts:** Long-running cells (e.g., model training) may timeout; rerun individual cells.
- **Local Execution:** If running locally, ensure Jupyter is installed (`pip install jupyter`) and navigate to the repo directory.

-----

## 💡 Key Findings

Based on the analysis of 412 trading days:

### 1. Risk-Adjusted Performance
- **Greed periods** show 2.1 times better risk-adjusted returns (0.177) than Fear periods (0.084).
- This challenges the idea that fear always means opportunity—Greed can be more efficient for traders.

### 2. Primary Behavioral Signal
- Using Random Forest, **total daily volume** is the top predictor of market sentiment (29.9% importance).
- Fear days have 4.2 times more volume, indicating high activity like capitulation or accumulation.

### 3. Strategic Recommendation
- Focus on handling volatility in Greed periods rather than avoiding them. Traders are less active but more aggressive, leading to better returns.
