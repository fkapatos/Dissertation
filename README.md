# Predicting Company Earnings Changes Using Large Language Models (LLMs)

This repository contains the full code and documentation for the undergraduate economics dissertation:

**"How Effective are Large Language Models at Predicting Companies’ Earnings Changes?"**  
Frangiskos Kapatos  
University of Nottingham, School of Economics

---

## 📊 Overview

This project investigates the use of Large Language Models (LLMs) such as GPT-4, GPT-4o-mini, and o3-mini to predict whether a company's earnings will increase or decrease in the next fiscal year, based purely on standardised and anonymised financial statement data (balance sheets and income statements). Inspired by Kim et al. (2024), this project replicates and extends their work by:

- Testing multiple prompting strategies (simple vs. Chain-of-Thought).
- Evaluating reasoning vs. non-reasoning models.
- Assessing the impact of historical data length (up to 8 years).
- Comparing performance to professional human financial analysts.

---

## 📦 Requirements

- Python 3.8+
- OpenAI Python SDK (`openai`)
- pandas
- requests
- IPython

```bash
pip install openai pandas requests ipython
