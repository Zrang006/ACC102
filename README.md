# ACC102 —— Automated Fund Audit Agent: Look-through ROE Analysis

## Project Overview
This project provides a robust Python-based analytical workflow for performing **look-through audits** on Chinese equity funds. Unlike traditional fund analysis that relies on NAV (Net Asset Value), this agent penetrates the fund's portfolio to evaluate the fundamental profitability (Return on Equity) of its underlying holdings using the **Wharton Research Data Services (WRDS) CSMAR database**.

The tool is designed for **auditors and quantitative analysts** to verify whether a fund's portfolio aligns with its stated investment strategy (e.g., Value vs. Growth) through direct accounting data.

## Key Features
- **Deep Penetration**: Automatically retrieves stock-level holdings for any given Mutual Fund or ETF in the China market.
- **Production-Grade Data**: Bypasses sample datasets to access full-scale financial tables (`fs_comins`, `fs_combas`) with 640,000+ records, ensuring 100% coverage for 2022-2024 periods.
- **Smart Schema Mapping**: Resolves CSMAR field code inconsistencies (e.g., mapping `b002100000` to Net Income) automatically.
- **Aggregation Logic**: Handles complex portfolio structures, such as feeder funds and multi-name stock entries, to ensure accurate weight calculations.
- **Professional Output**: Generates an audit-ready Excel report including Ticker, Stock Name, Portfolio Weight, and calculated ROE.

## Project Structure
- `audit_workflow.ipynb`: The primary Jupyter Notebook containing the Python implementation and step-by-step analysis.
- `README.md`: Project documentation and setup guide (this file).
- `CSMAR_Final_Audit_Success.xlsx`: A sample output report generated for the Southern Non-Ferrous Metals ETF (512400).
- `Reflection_Report.pdf`: Detailed project reflection and AI disclosure.

## User Customization
Users can audit any specific Chinese fund by simply updating the following variables in the **Configuration Cell**:
- `TARGET_FUND`: Input the 6-digit fund code (e.g., `510050` for SSE 50).
- `REPORT_DATE`: Specify the audit period (e.g., `2023-06-30`).

The agent's logic is designed to be **sector-agnostic**, meaning it will automatically adapt its audit process whether the target is a Consumer, Technology, or Commodity-based fund.

## Technical Stack
- **Language**: Python 3.x
- **Data Source**: WRDS CSMAR Database (PostgreSQL)
- **Libraries**: 
  - `wrds`: For database connectivity.
  - `pandas`: For data transformation and financial calculations.
  - `openpyxl`: For Excel report generation.

## How to Run
1. **Prerequisites**: Ensure you have a valid WRDS account with access to CSMAR libraries.
2. **Installation**:
   ```bash
   pip install wrds pandas openpyxl
