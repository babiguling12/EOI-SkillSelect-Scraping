# Main Execution Flow Documentation (`main.py`)

This is the entry point of the application. It imports the `SkillSelectScraper` and the `config`, orchestrating the step-by-step logic required to extract the data systematically.

## 🔄 Workflow Sequence

1. **Dashboard Initialization**: Opens the target URL and waits for the initial page loader to disappear.
2. **Parameter Configuration**: Navigates into the dashboard iframe and sets the required base parameters (Occupation = Yes, State = Yes, Points = No).
3. **Applying Global Filters**: Expands the Qlik filter panes to select specific Visa Types and EOI Statuses, locking these parameters globally for the session.
4. **Table Preparation**: Moves to the final data table view and locks in the first state (e.g., ACT) to prepare the UI for looping.
5. **Dynamic Month Extraction**: Reads the top "Current Selections" bar to scrape all available months. Falls back to `config.MONTHS` if extraction fails.
6. **Nested Extraction Loop (Months x States)**:
   * **Outer Loop (Months)**: Iterates through each extracted month, switching the global timeline parameter.
   * **Inner Loop (States)**: Iterates through the list of Australian states.
   * **Auto-Resume Check**: Before switching UI elements, it checks if the state/month CSV already exists. If yes, it skips to the next iteration, saving massive amounts of time.
   * **Download Execution**: If the data is missing, it updates the state filter, triggers the right-click export, and waits for the CSV conversion.
7. **Master Data Generation**: At the end of each month's loop, it selects *ALL* states simultaneously and downloads a compiled "Master Data" file for that specific month.
8. **UI Reset**: Carefully resets the Qlik active filters back to the first state before moving on to the next month to prevent selection overlapping.
9. **Cleanup**: Closes the browser cleanly once all loops are complete.