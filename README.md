# Store_Dashboard 
[🌐 **Open the live Streamlit app**](https://storedashboard-sells.streamlit.app/)  
Streamlit dashboard for retail sales analysis. Filter by date, category, payment method, and location. View KPIs, daily trends, channel breakdowns, and export filtered CSVs.

Table of contents
- Features
- Project structure
- Getting started
  - Prerequisites
  - Installation
  - Run locally
- Usage
- Data schema
- Validation & Common pitfalls
- Deployment (Streamlit Community Cloud)
- Troubleshooting
- License

## ✨ Features

- Summary KPIs: **Total Sales**, **Average Ticket**, **Quantity Sold**
- Sidebar filters: **Date range**, **Categories**, **Payment methods**, **Locations**
- Visualizations:
  - Daily trend of sales
  - Channel split: **Online vs In-Store**
  - Payment method distribution
  - Category distribution
- One-click CSV download of the currently filtered subset
- Lightweight, single-file Streamlit app (App.py) for easy customization

## 🧱 Project structure

- App.py
- requirements.txt
- data/retail_store_sales_clean.csv
- README.md
- LICENSE
- .gitignore

## 🚀 Getting started

### Prerequisites
- Python 3.11 (recommended)
- git (optional, to clone the repo)
- ~200 MB free disk (for virtualenv and dependencies)

### Installation (local)
1. Clone the repo:
   ```bash
   git clone https://github.com/DaniC01/Store_Dashboard.git
   cd Store_Dashboard
   ```
2. Create and activate a virtual environment:
   - Windows:
     ```powershell
     python -m venv .venv
     .venv\Scripts\Activate.ps1   # or .venv\Scripts\activate
     ```
   - macOS / Linux:
     ```bash
     python -m venv .venv
     source .venv/bin/activate
     ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

### Run locally
Start the Streamlit app:
```bash
streamlit run App.py
```
Open the URL shown by Streamlit (usually http://localhost:8501).

## ▶️ Usage

1. Pick a valid date range using the sidebar date selector.
2. Optionally select one or more categories, payment methods, and locations.
3. Read the KPIs at the top of the page.
4. Inspect charts below to analyze trends and distributions.
5. Click "Download filtered data" (or similar button) to export the current filtered dataset as a CSV.

Tips:
- If the dataset is large, restrict the date range first to speed up rendering.
- Use category and payment filters together to isolate segments (e.g., "Credit Card" in "Electronics").

## 📊 Data schema

The app expects a CSV file at data/retail_store_sales_clean.csv with at least these columns:

- Transaction Date (date) — column name: Transaction Date (or equivalent parseable date)
- Category (string)
- Payment Method (string)
- Location (string)
- Total Spent (numeric)
- Quantity (numeric)

Derived in the app:
- Channel: "Online" if Location == "online" (case-insensitive), else "In-Store"
- Calendar fields for grouping: year, month, day, weekday, etc.

If your column names differ, either:
- Modify the CSV headers to match the expected names, or
- Edit App.py to map your column names to the expected ones (look for the loading / rename section).

## ✅ Validation & Common pitfalls

- Ensure Transaction Date is parseable by pandas.to_datetime.
- Ensure numeric columns (Total Spent, Quantity) contain numeric data (no currency symbols).
- Location values should include "online" (lower/upper case) for channel detection, or adjust logic in App.py.

## 📦 Deployment (Streamlit Community Cloud)

To deploy:
- Repository: this project
- Branch: main
- App file: App.py
- Python version: 3.11

Steps:
1. Push your code to GitHub (main branch).
2. Open Streamlit Cloud (share.streamlit.io) and connect your GitHub account.
3. Select this repository and branch, set the app file to App.py and the Python version to 3.11.
4. Deploy.

If you use external data (not committed to the repo), add upload/download logic or connect to a cloud storage provider and configure secrets in Streamlit Cloud.


## 🆘 Troubleshooting

- Streamlit shows "ModuleNotFoundError": ensure virtualenv is activated and requirements.txt installed.
- Slow rendering: reduce the default date range or aggregate data before plotting.
- CSV download not working: confirm the download button code uses Streamlit's st.download_button with the correct bytes/text.

## 📜 License

MIT License — see LICENSE for details.
