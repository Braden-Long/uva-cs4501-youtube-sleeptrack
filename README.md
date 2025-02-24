# uva-cs4501-youtube-sleeptrack

This repository contains a tool for analyzing your sleep patterns using YouTube history data.  
It was developed as part of a CS4501 Data Privacy project at UVA.

## Overview

This tool processes your YouTube Takeout history data (in JSON format) to identify:
- **Sleep periods** (based on gaps in activity)
- **Daily and weekly viewing metrics** (e.g., total videos watched, estimated watch time)
- **Data plots** that visualize sleep boundary times, aggregated daily metrics, histograms, and scatter plots

All generated graphs are automatically saved in a subdirectory called `graphs`.

## How to Use

**Steps to Download and Process Your Own YouTube History Data:**

1. **Download YouTube Data from Google Takeout**
   - Go to [Google Takeout](https://takeout.google.com/settings/takeout)
   - Click **"Deselect all"**.
   - Select only **YouTube**.
   - Click on **"All YouTube data included"** and force-select only the **"history"** content.
   - Under **"Multiple formats"**, find the **"history"** section and change the dropdown from **HTML** to **JSON**.
   - Click **"Next step"** and then **"Create export"**.
   
2. **Extract the Takeout ZIP File**
   - After the export is ready, download and unzip the file.
   - Locate the **"history"** directory within the extracted files.

3. **Setup the Repository**
   - Copy the **"history"** directory to the same directory as the provided code file (`youtube_sleeptrack.ipynb` or `youtube_sleeptrack.py`).

4. **Run the Code**
   - It is recommended to use the Jupyter Notebook version (`.ipynb`) for interactive use.
   - Alternatively, you can run the Python script version.
   - Adjust the date ranges within the code (variables like `start_range`, `end_range`, or custom last-month ranges) if you want to analyze a specific time period.

5. **View the Graphs**
   - After running the code, all generated graphs will be saved in the `graphs` subdirectory.
   - Check these graphs to better understand your sleep patterns and viewing metrics.

## Data Plots Description & How to Interpret Them

The code generates several plots that provide insight into your YouTube viewing habits and inferred sleep patterns:

1. **Weekly Average Sleep Boundary Times (6 Months)**
   - **What it shows:**  
     A line plot with **Week Index** on the x-axis and **Time of Day (EST)** on the y-axis. Two lines are plotted:
     - **Final Video Time Before Sleep (EST):** The average time (per week) of your last YouTube activity before a detected sleep period.
     - **First Video Time After Sleep (EST):** The average time (per week) of your first YouTube activity after waking up.
   - **Interpretation:**  
     These lines give an indication of your general sleep and wake times over the 6-month period (in 24-hour EST format).

2. **Daily Sleep Boundary Times (Last Month)**
   - **What it shows:**  
     A daily plot over a custom one-month period (e.g., 2025-01-09 to 2025-02-09) showing:
     - **Final Video Time Before Sleep (EST)**
     - **First Video Time After Sleep (EST)**
   - **Interpretation:**  
     This plot visualizes day-to-day variations in your sleep boundaries over the selected month.

3. **Daily Aggregated Metrics (6 Months)**
   - **What it shows:**  
     A four-panel subplot:
     - **Panel 1:** Total videos watched per day.
     - **Panel 2:** Total watch time per day (derived from capped inter-event gaps, in minutes).
     - **Panel 3:** Average inter-event duration (in seconds), which estimates the average video “length” based on gaps between events (capped at 15 minutes).
     - **Panel 4:** Video length differential (difference between the first and last inter-event duration).
   - **Interpretation:**  
     These metrics help reveal trends in your YouTube usage over time, such as overall engagement, watch time distribution, and potential changes in viewing behavior throughout the day.

4. **Daily Metrics (Last Month)**
   - **What it shows:**  
     A two-panel subplot for the selected last month:
     - **Panel 1:** Total videos watched each day.
     - **Panel 2:** Total watch time (in minutes) per day.
   - **Interpretation:**  
     This plot focuses on daily variations in your YouTube usage for the chosen one-month period.

5. **Histogram of Video Length Differential (6 Months)**
   - **What it shows:**  
     A histogram plotting the distribution of video length differential (in seconds) calculated each day.
   - **Interpretation:**  
     The histogram provides insight into the variability of video viewing behavior over days, which may reflect different content types or usage habits.

6. **Histogram of Inferred Sleep Durations (6 Months)**
   - **What it shows:**  
     A histogram of the inferred sleep durations (in hours) based on detected gaps.
   - **Interpretation:**  
     This distribution helps you identify common sleep duration patterns and possible outliers (e.g., excessively long inferred sleep periods).

7. **Scatter Plot: Final Video Time vs. Sleep Duration (EST)**
   - **What it shows:**  
     A scatter plot with:
     - **X-axis:** Final Video Time Before Sleep (in EST, in 24-hour format).
     - **Y-axis:** Sleep Duration (in hours).
     - A trend line (calculated after filtering out sleep durations over 12 hours, which are considered outliers).
   - **Interpretation:**  
     This plot helps explore the relationship between the time you finish watching videos and the duration of your sleep. The trend line can indicate whether later sleep times correspond to longer or shorter sleep durations.

## Customization

- **Time Range Adjustments:**  
  The code includes default date ranges (e.g., a 6-month period and a specific one-month range). Modify these ranges in the code for your data.

- **Filter Constraints:**  
  The sleep period detection uses thresholds (e.g., final video time between 2–7 AM and wake-up time between 10 AM–2 PM). Feel free to adjust these based on your personal habits.

## File Structure

- `youtube_sleeptrack.ipynb` / `youtube_sleeptrack.py`  
  The main analysis code (choose the version you prefer).

- `history/`  
  Directory that contains the YouTube history JSON files as exported from Google Takeout.

- `graphs/`  
  **(Automatically created)**  
  Directory where all generated graphs are saved.

## License

This project is provided under the terms of the MIT License.

---

Enjoy exploring your YouTube sleep patterns!