***PERSONAL PRODUCTIVITY ANALYZER (PPA)***

`Goal`
Use data from your daily digital activities (coding, phone usage, browsing, etc.) to understand, predict, and improve your productivity patterns.


`Project Workflow Overview`
|Stage	        | Description	                                          |Output |
|-----------------|--------------------------------------------------------|---------|
|Data Collection |	Gather daily activity data (screen time, coding hours, sleep, etc.)|	Raw CSV/DB logs|
|Data Storage	|Store, clean, and format your tracked data for analysis|	Cleaned dataset|
|Analysis & Modeling	|Perform EDA, build predictive and recommendation models|	ML model + metrics|
|Visualization & Dashboard	|Streamlit dashboard for trends, focus prediction, and recommendations	|Deployed ap|


`Tech Stack`
| Layer                     | Tool                                                                    | Purpose                             |
| ------------------------- | ----------------------------------------------------------------------- | ----------------------------------- |
| **Data Collection**       | `Python`, `RescueTime API`, `Google Digital Wellbeing`, `manual logger` | Collect daily activity data         |
| **Data Storage**          | `pandas`, `SQLite`                                                      | Store & structure time-series data  |
| **Data Analysis**         | `NumPy`, `pandas`, `matplotlib`, `seaborn`                              | Perform EDA and feature engineering |
| **Modeling**              | `scikit-learn`, `Prophet`, or `XGBoost`                                 | Predict focus/productivity levels   |
| **Visualization**         | `Streamlit`, `Plotly`                                                   | Build an interactive dashboard      |
| **Automation (optional)** | `cron`, `schedule` (Python lib)                                         | Automate daily data collection      |
| **Version Control**       | `GitHub`                                                                | Track code and progress             |
| **Documentation**         | `Notion` / `README.md`                                                  | Log insights, assumptions, findings |


`Data Sources`
| Source                                 | Description                                                               | Integration Method                                           | Example Data                                                       |
| -------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------------ |
| **RescueTime API**                     | Tracks app usage, websites, coding tools, and productivity scores         | API key (free tier available)                                | `timestamp, category, productivity_score, duration`                |
| **Google Digital Wellbeing (Android)** | Provides screen time by app, unlocks, and notifications                   | Manual export or local script via Android Debug Bridge (ADB) | `app_name, screen_time, start_time, end_time`                      |
| **Manual CSV Logging**                 | You record data daily (e.g., coding hours, sleep, exercise, distractions) | Simple Python script or Google Form → CSV                    | `date, coding_hours, sleep_hours, social_media_hours, focus_score` |
| **Optional Integrations**              | Toggl (for work sessions), Notion API, Fitbit                             | API calls                                                    | Activity logs, heart rate, etc.                                    |

`Step-by-step pipeline`
- 🧾 `Stage 1: Data Collection`

Script runs daily (or manual input)

Fetch data from:

RescueTime API → JSON response → CSV/SQLite

Manual logs (append to CSV)

Each record includes:

Timestamp, activity type, duration, productivity score, category

🧹 `Stage 2: Data Cleaning & Preprocessing`

Parse timestamps into datetime objects

Resample data (hourly/daily)

Handle missing values (e.g., if a day wasn’t tracked)

Feature engineering:

total_focus_hours

distraction_ratio = (unproductive_time / total_time)

sleep_hours or exercise (from manual log)

📈 `Stage 3: Exploratory Data Analysis (EDA)`

Identify:

Most productive hours

Weekday vs weekend patterns

Correlation between sleep and focus

Visuals:

Heatmaps (hour vs productivity)

Line charts (productivity trend over time)

Bar plots (activities contributing to distraction)

🤖 `Stage 4: Modeling`

Define a focus score (e.g., ratio of productive time / total time)

Predict next-day focus using:

Regression: LinearRegression, RandomForestRegressor

Evaluate:

MAE, RMSE for prediction accuracy

Output:

“Predicted Focus Score” for next day

“Optimal work hours” recommendation

📊 `Stage 5: Visualization / Dashboard`

Build Streamlit dashboard with:

Productivity calendar view

Time-of-day heatmap

Next-day focus forecast

Personalized recommendations (“e.g. Best time to start coding: 9–11 AM”)

Update dashboard daily (auto or manual refresh)

🔁 `Stage 6: Feedback Loop`

Record daily performance against prediction

Fine-tune model weekly using new data

Add self-experiments (e.g., “Try early work hours” → measure change)