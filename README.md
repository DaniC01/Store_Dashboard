# Store_Dashboard
Streamlit dashboard for retail sales analysis. Filter by date, category, payment method, and location. KPIs, daily trends, channel breakdown, and CSV export.

✨ Features

KPIs: Total Sales, Avg. Ticket, Quantity Sold

Sidebar filters: date range, categories, payment methods, locations

Daily trend line, channel split (Online vs In-Store), payment and category distributions

One-click CSV download of the filtered subset

🧱 Project structure
.
├─ App.py
├─ requirements.txt
├─ retail_store_sales_clean.csv
├─ README.md
├─ LICENSE
└─ .gitignore

📦 Installation
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate

pip install -r requirements.txt

▶️ Run locally
streamlit run App.py

📊 Data schema

Required columns in data/retail_store_sales_clean.csv:

Transaction Date (date)

Category (string)

Payment Method (string)

Location (string)

Total Spent (numeric)

Quantity (numeric)

Derived in the app:

Channel = Online if Location == "online", else In-Store

Calendar fields like day and month for grouping

🖥️ Usage

Pick a valid date range.

Select categories, payment methods, and locations.

Read KPIs and inspect charts.

Click Download filtered data to export CSV.

🚀 Deploy (Streamlit Community Cloud)

Repo: this project

Branch: main

App file: App.py

Python: 3.11


🏷️ Topics

streamlit, retail-analytics, data-visualization, python, dashboard

📜 License

MIT License. See LICENSE.
