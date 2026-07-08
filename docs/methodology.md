📄 Methodology
1. Overview
This document outlines the analytical methodology used to build the YouTube Music Engagement Dashboard, including data preparation, transformation logic, modeling decisions, and visualization strategy. The goal is to provide transparency into how insights were derived and how the dashboard supports decision‑making for content performance and audience engagement.

2. Data Sources
The dataset originates from YouTube Analytics, exported as CSV files. Key tables include:
- Video Performance Data
- Views
- Likes
- Comments
- Shares
- Watch time
- Audience retention metrics
- Channel-Level Metrics
- Subscribers gained/lost
- Traffic sources
- Playback locations

3. Data Cleaning & Preparation
Data cleaning was performed using Power BI’s Power Query Editor. Key steps include:

✔ Standardizing column names
Converted inconsistent naming conventions into a clean, readable format.

✔ Removing null and duplicate records
Ensured accuracy and consistency across all metrics.

✔ Converting data types
- Dates → Date
- Views, likes, comments → Whole number
- Watch time → Decimal

  ✔ Creating derived fields
Examples:
- Engagement Rate = (Likes + Comments + Shares) / Views
- Retention % = Average View Duration / Video Length

4. Data Modeling
A star-schema inspired model was used to ensure clarity and performance.

✔ Fact Table
- fact_video_metrics  
- Contains all numerical measures such as views, likes, comments, watch time, and engagement.

✔ Dimension Tables
- dim_video — video title, category, publish date
- dim_channel — channel metadata
- dim_date — calendar table for time intelligence

✔ Relationships
- dim_video → fact_video_metrics (1-to-many)
- dim_date → fact_video_metrics (1-to-many)
This structure supports flexible slicing by date, video, and channel attributes.

5. DAX Measures
Key measures created to support dashboard insights:
- Engagement Rate
<img width="320" height="121" alt="image" src="https://github.com/user-attachments/assets/bbe9c4a5-7c83-4cb7-a266-8c3cbe50a75f" />

- Average View Duration
<img width="427" height="52" alt="image" src="https://github.com/user-attachments/assets/6ad1e231-e59c-4db0-bdf7-187b4ca94f0d" />

- Retention Percentage
<img width="317" height="132" alt="image" src="https://github.com/user-attachments/assets/594cdfd7-c5ff-4d0f-9dba-c840bf161f0d" />
  
- Total Engagement
<img width="457" height="53" alt="image" src="https://github.com/user-attachments/assets/23ccfd8a-fcac-4bc2-8492-6c95d3d9551c" />

These measures power the KPI cards and comparative visuals.

6. Dashboard Design Approach
The dashboard is structured into three pages, each serving a specific analytical purpose.

Page 1 — Overall Performance
Focuses on high-level KPIs:
- Total views
- Total engagement
- Average retention
- Top-performing videos

Page 2 — Channel Performance
Highlights:
- Subscriber trends
- Traffic sources
- Playback locations
- Channel growth indicators

Page 3 — Engagement Overview
Provides deeper insight into:
- Likes distribution
- Comment patterns
- Engagement breakdown by video
- Treemap of top-engaged content
- Design principles used:
- Minimalist layout
- Consistent color palette
- Clear hierarchy of information
- KPI-first storytelling

7. Limitations
- Data reflects only YouTube Analytics exports; external platforms are not included.
- Engagement metrics may vary depending on YouTube’s algorithmic updates.
- Viewer demographics were not included due to dataset constraints.

8. Future Improvements
- Add demographic insights (age, geography, gender).
- Integrate YouTube API for automated data refresh.
- Add predictive modeling (e.g., engagement forecasting).
- Include sentiment analysis for comments.

