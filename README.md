

## 1. Project Overview

This project uses the **UCI Online Retail dataset** to build a professional Power BI dashboard. The raw e‑commerce transaction data was cleaned and transformed using **Power Query** in Power BI, followed by data modeling, DAX measures, and interactive visuals to highlight revenue, orders, customers, and product performance across countries.

**Key deliverables**

* Cleaned dataset (in Power Query, applied transformations)
* Power BI report (`.pbix`) with an executive dashboard layout
* Project documentation, screenshots, and workflow description

---

## 2. Repo Structure (recommended)

```
uci-online-retail-dashboard/
├── data/
│   └── raw/Online_Retail.csv            # original raw dataset (from UCI)
├── powerbi/
│   ├── UCI_Online_Retail_Report.pbix    # Power BI report
├── screenshots                          # dashboard images for README
└── README.md
```

**Why this structure?**

* `data/raw` keeps the original dataset.
* `powerbi` contains the final report and theme.
* `screenshots` holds visuals for easy reference.

---

## 3. Dataset Notes (columns & quick facts)

The UCI Online Retail dataset contains:

* `InvoiceNo` — Invoice number (canceled invoices usually start with 'C').
* `StockCode` — Product code.
* `Description` — Product description.
* `Quantity` — Number of items (can be negative for returns).
* `InvoiceDate` — Date and time of transaction.
* `UnitPrice` — Price per item.
* `CustomerID` — Unique customer ID (may contain NULLs).
* `Country` — Country name (e.g., United Kingdom, Germany).

---

## 4. Workflow (Step-by-step)

### Step 1 — Download dataset

* Download `Online Retail.csv` from the UCI Machine Learning Repository and save in `data/raw/`.

### Step 2 — Data Cleaning in Power Query

Performed directly in Power BI:

* **Filtered valid transactions** → kept rows with `Quantity > 0` and `UnitPrice > 0`.
* **Handled missing values** → dropped rows with missing `CustomerID` or `InvoiceDate`.
* **Created new column** → `Revenue = Quantity * UnitPrice`.


### Step 3 — DAX Measures

Created measures to drive KPIs and visuals:

```DAX
Total Revenue = SUMX('OnlineRetail', 'OnlineRetail'[Quantity] * 'OnlineRetail'[UnitPrice])
Total Orders = DISTINCTCOUNT('OnlineRetail'[InvoiceNo])
Total Customers = DISTINCTCOUNT('OnlineRetail'[CustomerID])
Average Order Value = DIVIDE([Total Revenue], [Total Orders], 0)
```

### Step 4 — Dashboard Layout

Following a clean executive layout:

* **Top KPIs:** Total Revenue (in M), Total Orders, Total Customers, Average Order Value.
* **Line Chart:** Revenue Trend by Month.
* **Map:** Revenue & Customers by Country.
* **Donut Chart:** Customer Distribution by Country.
* **Bar Chart:** Top Products by Revenue.
* **Treemap:** Revenue Share by Product.
* **Slicers (side panel):** Invoice Date, Country, CustomerID.

### Step 5 — Design & Theme

* Used a consistent clear font(Segoe UI Semibold).
* Grouped slicers in a left-side panel.
* Applied color background in canvas.

### Step 6 — Publish and Share

* Saved the `.pbix` file.
* Published to Power BI Service for interactive viewing.
* Added screenshots in `screenshots`.

---

## 5. Visual & Dashboard Best Practices

* Uniform KPI cards at the top.
* Consistent color palette across charts.
* Clear, concise titles: e.g., *“Revenue Trend by Month”*, *“Top Products by Revenue”*.
* Drilldowns enabled for interactivity.

---

## 6. Dataset

* Dataset source: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/online+retail).

---


