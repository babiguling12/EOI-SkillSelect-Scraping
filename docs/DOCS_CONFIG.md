# Configuration File Documentation (`config.py`)

This file acts as the central brain for all static variables, settings, and XPath locators used across the scraping project. By isolating these variables, it ensures that if the target website updates its UI, you only need to update the locators here without touching the core logic.

## ⚙️ General Settings

* **`BASE_DIR` & `DOWNLOAD_DIR`**: Automatically sets the current working directory and creates a `DATASET` folder to store all downloaded files.
* **`URL`**: The direct link to the Australian SkillSelect EOI Qlik Sense dashboard.
* **`HEADLESS`**: A boolean (`True`/`False`) that toggles whether Google Chrome runs in the background (Headless mode) or opens a visible window.
* **`MONTHS` & `STATES`**: Fallback lists used in case the dynamic extraction of months or states fails from the dashboard UI.

## 🎯 XPath Selectors Directory

The file categorizes XPath selectors into logical groups to easily interact with the Qlik Sense DOM:

1. **Iframe & Navigation**: Locators for the main Qlik iframe (`XPATH_IFRAME`) and top bar navigation buttons.
2. **Parameter Settings (Yes/No)**: Precision locators for toggling initial survey parameters like Occupations, Points, and Nominated State.
3. **Global Filters**: Locators for expanding dropdown menus and specific locators to select Visa Types (189, 190, 491) and EOI Statuses (Submitted, Invited, Lodged, etc.).
4. **Current Selections & State Filtering**: Locators targeting the top active selection bar to switch between different States and Months dynamically during the scraping loop.
5. **Data Export Context Menu**: Specific locators to find a table cell, trigger the Right-Click menu, and click the Qlik Sense native "Export data" button and download link.