# Workout-Progress-Analysis
> This project is being developed iteratively. Each version documents progress, reasoning, and next steps as I build out a full data analysis pipeline using Python and Pandas.

---

## Workout Progress Analysis

### Project Overview
This project consolidates three years (2022–2025) of personal workout data to analyze training progression across all major muscle groups. The dataset was engineered from multiple extracted metrics — total load, total sets, total reps, and weight per rep — to reveal long-term strength and performance trends. 

The analysis and visualizations were conducted using Python (Pandas, Matplotlib, Seaborn), providing a full data analytics workflow from transformation to insight generation.

---

### Objectives
- Engineer multiple training metric tables and merge them into one analytical dataset.  
- Track strength and volume progression across muscle groups over time.  
- Identify peak performance periods and plateaus.  
- Visualize 8-week block progressions for better periodization insights.

---

### Dataset Engineering
Two original raw datasets were used to generate **four derived tables** based on key training metrics:

| Table | Purpose | Columns (9 total each) |
|-------|----------|------------------------|
| **Total_Load** | Tracks cumulative load per session | Chest, Upper Back, Triceps, Lats, Traps, Biceps, Quads, Hamstrings, Calves |
| **Total_Sets** | Total number of sets completed per muscle group | Same 9 columns |
| **Total_Reps** | Total repetitions performed per session | Same 9 columns |
| **Weight_Per_Rep** | Weight lifted per repetition across exercises | Same 9 columns |

Each metric table contained **data for all nine major muscle groups**, capturing full-body workload balance. After cleaning and standardization, they were **merged into a unified dataset** that powers the entire analysis.

---

### Tech Stack
- **Language:** Python  
- **Libraries:** Pandas, NumPy, Matplotlib, Seaborn  
- **Tools:** Jupyter Notebook, VS Code, Google Colab  
- **Workflow:** Automated ETL pipeline (Extract → Transform → Merge → Analyze)  
- **Visualization:** Tableau  

---

### Automation Script
The project automates the process of transforming raw workout logs into a clean, merged analytical dataset.

**Workflow Highlights:**  
1. Reads raw input files dynamically.  
2. Cleans, standardizes, and aggregates data per metric type.  
3. Outputs eight metric tables (four per dataset).  
4. Merges all tables into one **final analytical dataset** for visualization and trend analysis.


**Example Snippet:**
```python
# Automatically rename weeks into structured blocks
df = auto_rename_weeks(df)
df2024 = auto_rename_weeks(df2024, block_sizes=[8,8,8,8,4])

# Create metric tables for all muscles
tables_2022 = create_metric_table(df, muscles_2022)
tables_2024 = create_metric_table(df2024, muscles_2024)

# Clean and prepare tables for analysis
tables_2022_cleaned = {metric: prepare_metric_table(tables_2022, metric) for metric in metrics}
tables_2024_cleaned = {metric: prepare_metric_table(tables_2024, metric) for metric in metrics}

# Merge datasets automatically
the_merged = {metric: pd.concat([tables_2022_cleaned[metric], 
                                 tables_2024_cleaned[metric]], ignore_index=True)
              for metric in metrics}
```
## 🧾 File Structure
/Workout-Progress-Analysis
│
├── data/
│   ├── raw/                     # Original input CSV files (2022–2023.csv, 2024–2025.csv)
│   ├── processed/               # Generated metric tables (Total Load, Sets, Reps, Weight Per Rep)
│   └── merged_dataset.csv       # Final merged dataset for analysis
│
├── notebooks/
│   ├── automation_pipeline.ipynb       # Full ETL workflow and metric table creation
│   ├── analysis_visualization.ipynb    # Exploratory data analysis, plots, and trends
│
├── scripts/
│   └── automate_metrics.py             # Python functions for automated data cleaning & table generation
│
├── visuals/                             # Exported charts, histograms, and heatmaps
│
└── README.md                            # Project documentation
Link for Tableau: (https://public.tableau.com/views/WorkoutSheet/Dashboard1?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)(https://public.tableau.com/views/WorkoutAnalyticsVisualization/WorkoutProgressDashboard?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)
