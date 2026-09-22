# 📈 Financial Portfolio Risk & Performance Dashboard

## 🎯 Project Overview

This is an end-to-end Data Analytics and ETL (Extract, Transform, Load) project. The goal of this project is to track the performance and risk metrics of a custom portfolio of Indian stocks (RELIANCE, TCS, INFY, HDFCBANK). It automates the extraction of live stock market data, cleans it using Python, stores it in a MySQL database, and visualizes the insights using Power BI.

## 🏗️ Architecture & Data Pipeline

To make the data pipeline efficient and production-ready, the data loading process is divided into two logical phases:

### Phase 1: Historical Data Load (Base Setup)

- **Objective:** To build the foundational database.
- **Process:** Fetched 1 year of historical stock data using the `yfinance` API. The data was processed, flattened, and initially saved into a CSV format before being pushed to the MySQL database.
- **Status:** Executed once.

### Phase 2: On-Demand Execution:
The Python script (daily_stock_update.py) is triggered manually to fetch the latest market closing data.
Data Transformation & Load: It cleans the data in memory, handles timezone formatting, and appends the fresh rows to the existing MySQL table using SQLAlchemy.
Dashboard Refresh: Power BI is refreshed to instantly update the visualizations, ROI, and volatility metrics based on the newly added database rows.

## 🛠️ Tech Stack Used

- **Data Extraction & Transformation:** Python (`yfinance`, `pandas`)
- **Database Management:** MySQL (`sqlalchemy`, `pymysql`)
- **Data Visualization:** Power BI (DAX, Interactive Dashboards)

## 📂 Repository Structure

- `daily_stock_update.py` - The main ETL script for fetching and appending daily live data.
- `Stock_Market_Dashboard.pbix` - The Power BI file containing the data model and visualizations.
- `dashboard_preview.png` - A high-quality snapshot of the final dashboard.
- _(Note: Phase 1 initial extraction scripts are archived locally as they are no longer needed for daily operations)._

## 📊 Key Dashboard Metrics

- **Latest Price & Portfolio Value:** Real-time tracking of asset worth.
- **ROI Percentage:** Return on Investment calculated against historical baselines.
- **50-Day Moving Average vs Closing Price:** Trend analysis chart.
- **20 Days Volatility Risk:** A gauge chart indicating current market risk based on recent fluctuations.

## 🚀 How It Works (Daily Flow)

1. Python script connects to the Yahoo Finance API.
2. Extracts today's closing metrics for the selected tickers.
3. Cleans and transforms the data payload.
4. Appends the new rows securely into the MySQL `indian_stocks_data` table.
5. Power BI reads the updated database and refreshes the visual dashboard.
