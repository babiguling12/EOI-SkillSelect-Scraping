# Australian SkillSelect EOI Data Scraper

An automated web scraping tool built with Python and Selenium to extract Expression of Interest (EOI) data from the official Australian Department of Employment's Qlik Sense dashboard. 

Because Qlik Sense dashboards are highly dynamic and notoriously difficult to scrape via traditional HTTP requests, this bot automates the browser interactions—navigating iframes, applying complex filters, extracting dynamic dropdowns, and utilizing the native "Right-Click -> Export" functionality to download the data.

## ✨ Features

* **Dynamic Data Extraction**: Automatically scrolls and extracts available months directly from the dashboard UI, with a fallback list just in case.
* **Smart Export & Conversion**: Triggers the Qlik Sense right-click context menu to export data as `.xlsx`, waits for the download, and automatically converts it to `.csv` using Pandas for lighter storage and easier data analysis.
* **Auto-Resume Capability**: Checks if a specific file for a state and month already exists. If the script stops or fails, it will resume exactly where it left off without re-downloading existing data.
* **Data Enrichment**: Automatically injects `Nominated State` and `As At Month` columns into the final CSV files since the raw exported table sometimes lacks this context.
* **Organized Storage**: Automatically categorizes downloaded datasets into structured directories (`DATASET/YYYY/MM_YYYY/`).
* **Headless Support**: Can run quietly in the background (Headless Chrome) or visually for debugging purposes.

## 📂 Output Structure

The scraper automatically organizes the exported data by year and month. The output will look like this:

```text
📁 DATASET/
├── 📁 2026/
│   ├── 📁 01_2026/
│   │   ├── Data_EOI_ACT_01_2026_1710000000.csv
│   │   ├── Data_EOI_NSW_01_2026_1710000010.csv
│   │   ├── ...
│   │   └── MASTER_DATA_EOI_01_2026_1710000080.csv
│   ├── 📁 02_2026/
│   │   ├── Data_EOI_ACT_02_2026_1710000090.csv
│   │   └── ...