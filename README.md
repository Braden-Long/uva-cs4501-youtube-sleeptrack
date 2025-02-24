# uva-cs4501-youtube-sleeptrack

This repository contains a tool for analyzing your sleep patterns using YouTube history data.
It was developed as part of a CS4501 Data Privacy project at UVA.

## Overview

This tool processes your YouTube takeout history data (in JSON format) to identify:
- Sleep periods (based on gaps in activity)
- Daily and weekly viewing metrics (e.g., total videos watched, estimated watch time)
- Graphs that visualize sleep boundary times, aggregated daily metrics, histograms, and scatter plots

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
   - Adjust the date ranges within the code if you want to analyze a specific time period.

5. **View the Graphs**
   - After running the code, all generated graphs will be saved in the `graphs` subdirectory.
   - Check these graphs to understand your sleep patterns and viewing metrics.

## Customization

- **Time Range Adjustments:**  
  The code includes default date ranges (e.g., a 6-month period or a specific one-month range).  
  Modify these ranges in the code (look for variables like `start_range`, `end_range`, or custom last-month ranges) if needed.

- **Filter Constraints:**  
  The sleep period detection uses constraints (e.g., final video time between 2–7 AM, wake-up time between 10 AM–2 PM).  
  Feel free to modify these thresholds in the code according to your personal usage patterns.

## File Structure

- `youtube_sleeptrack.ipynb` / `youtube_sleeptrack.py`:  
  The main analysis code (use the version you prefer).

- `history/`:  
  Directory that contains the YouTube history JSON files as exported from Google Takeout.

- `graphs/`:  
  **(Automatically created)**  
  Directory where all generated graphs will be saved.

## License

This project is provided under the terms of the MIT License.

---

Enjoy exploring your YouTube sleep patterns!