# 📘 User Guide

## 📌 Overview

This guide walks you through how to use the two core scripts in this repository:

1. `data_cleaning_extraction.py` – For gathering and preparing financial data.
2. `earnings_prediction.py` – For predicting future earnings direction using LLMs.

---

## ⚙️ Step 1: Environment Setup

Install the required packages using pip:

```bash
pip install openai pandas requests ipython
```

You will need two API keys:
- An **OpenAI API key**
- A **FinancialModelingPrep API key**

Replace the placeholders (`"APIKEY"` and `api_key=""`) in the scripts with your actual API keys.

---

## 🧼 Step 2: Clean and Extract Financial Data

Run the following Python script to gather and format financial data from FinancialModelingPrep:

```bash
python data_cleaning_extraction.py
```

This script:
- Downloads 8 years of balance sheet and income statement data per firm.
- Maps raw data fields to readable accounting line items.
- Filters out firms with incomplete history.
- Anonymises company names and fiscal years (e.g., `FirmA`, `t`, `t-1`, etc.).
- Outputs a structured CSV file for use in the prediction phase.

💡 You can display the resulting dataframe using:

```python
from IPython.display import display
display(final_df)
```

---

## 🔮 Step 3: Predict Earnings Direction Using LLMs

Once you’ve generated your CSV, run:

```bash
python earnings_prediction.py
```

This script will:
- Read the anonymised financial CSV file.
- For each firm, construct a prompt using its 8 years of data.
- Use a **Chain-of-Thought** (CoT) system prompt to guide the LLM.
- Stream the LLM’s response, which includes reasoning and a final prediction.
- Collect and print results in a DataFrame.

---

## ⚡ Example Output (Terminal)

```
=== o3-mini ===
Firm: FirmB
LLM Prediction: increase
Time taken: 7.42 seconds
```

Final predictions are stored in a pandas DataFrame (`results_df`) with:
- The firm ID
- The full LLM response (reasoning)
- The final predicted direction: `increase` or `decrease`

You can export this with:

```python
results_df.to_csv("predictions_output.csv", index=False)
```

---

## 🔄 Switching Models

Inside `earnings_prediction.py`, you can change this line:

```python
llm_text = stream_model_output("o3-mini", system_prompt_template, user_prompt)
```

To use other models like:

- `"gpt-4"`
- `"gpt-4o-mini"`
- `"gpt-3.5-turbo"`
*(make sure your OpenAI API account supports these models and that you have enough credits - be concsious of API costs, especially with the more expensive reasoning (o-series) models, it may be better to use a "mini" model when testing)*

---

## 📁 Outputs

- Full streamed LLM reasoning for each firm.
- Final one-word prediction: `increase` or `decrease`.

---

## 🔍 Example Prompt Used (Chain-of-Thought)

The LLM is instructed using a detailed financial analyst-style prompt like:

```
You are a financial analyst tasked with analysing a company’s balance sheet and income statement to predict whether its earnings will increase or decrease in the next fiscal year...
```

It is then guided to:
- Spot trends in Revenues, COGS, Net Income, Assets, Liabilities, Equity
- Calculate financial ratios (e.g., Gross Margin, ROA, Current Ratio)
- Generate hypotheses and give a final verdict.

Full prompt templates are located in `earnings_prediction.py`.

---

---

## 📬 Contact

For questions, feel free to message me
