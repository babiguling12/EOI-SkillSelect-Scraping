# 🚀 Installation & Setup Guide

Follow these steps to set up the environment and run the scraper on your local machine.

## 📋 Prerequisites

To run this scraper successfully, you need:
* **Python 3.8+** installed on your machine.
* **Google Chrome** browser installed. *(Note: Selenium Manager handles the ChromeDriver automatically in modern Selenium versions).*

## 🛠️ Step-by-Step Installation

### 1. Clone the Repository
First, clone this repository to your local machine using Git:

```bash
git clone [https://github.com/babiguling12/EOI-SkillSelect-Scraping.git](https://github.com/babiguling12/EOI-SkillSelect-Scraping.git)
cd EOI-SkillSelect-Scraping
```

### 2. Create a Virtual Environment (Recommended)
It is highly recommended to use a virtual environment to isolate the project dependencies and avoid conflicts with other Python projects.

**For Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```

**For macOS/Linux:**
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies
Once your virtual environment is activated, install all the required libraries using `pip`. 

Ensure you have a `requirements.txt` file with the following content:
```text
selenium>=4.10.0
pandas>=2.0.0
openpyxl>=3.1.2
```

Run this command to install them:
```bash
pip install -r requirements.txt
```

### 4. Run the Scraper
With your virtual environment activated, start the scraping process by running:

```bash
python main.py
```

Sit back and let the bot navigate the dashboard. If you set `HEADLESS = False` in `config.py`, you will see the Chrome browser opening and performing the actions automatically.