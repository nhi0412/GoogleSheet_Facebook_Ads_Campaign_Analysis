# GoogleSheet_Facebook_Ads_Campaign_Analysis
# **1. Project Introduction**

### **Project Motivation**

This project evaluates the performance of Facebook advertising campaigns with a focus on optimizing CPM (Cost per Message) below the target of 25,000 VND. It includes dynamic filters for location and date, allowing marketing stakeholders to monitor campaign efficiency in real time through an interactive dashboard.

### **Project Goal**

With rising digital marketing costs, marketers need to make data-backed decisions that minimize cost while maintaining engagement. The main goal behind this project is to:

- Identify campaigns that exceed or underperform the target CPM threshold.
- Highlight the most cost-efficient campaigns to scale.
- Uncover patterns from CTR, CPC, messaging performance, and ad spend.

# **2. Dataset Overview**

## **Raw Data**

The raw dataset includes:

- Campaign performance by day
- Core metrics: Reach, Impressions, Amount Spent, CTR, CPC, CPM, Messaging Conversations Started

## **AggData** – Add Location for Segmentation

Used an `ArrayFormula` to classify campaigns by location:

```
excel

=ARRAYFORMULA(IFERROR(IFS(
  REGEXMATCH(E2:E, "HEAD"), "HEAD",
  REGEXMATCH(E2:E, "Q7"), "Q7",
  REGEXMATCH(E2:E, "Q2"), "Q2"
), "HEAD"))
```

This enabled geographic performance analysis across HEAD, Q7, Q2.

## **Interactive Data**

Created a filtered dataset based on user needs:

- Filters by:
    - Location
    - Date Range

## Pivot Table

After preparing the Interactive Data with filters for Location and Date Range, the next step involved building Pivot Tables to serve as the data source for dynamic dashboard visualizations.

# **3. Visualizations**

## Interactive Filters (Location & Date)

The dashboard includes fully interactive controls that allow users to filter ad performance dynamically, enabling focused insights across time and region.

### 1. Location Filter (Dropdown Menu)

- A dropdown menu (using Data Validation) allows users to select from:
    - `All` – View campaigns across all regions
    - `HEAD`, `Q7`, `Q2` – Filter data for specific geographic areas
- This filter dynamically updates all dependent metrics and charts, including:
    - Scorecards
    - Daily spend, Daily Mess, Daily Cost per Message
    - Top campaign tables
        
        ![Image](https://github.com/user-attachments/assets/456a42d1-8040-43a5-8d04-3e7616034055)
        

### **2. Date Range Picker**

- Start Date and End Date use Google Sheets' native date pickers for a clean user experience.
- Upon changing either date, formulas and charts instantly recalculate.
    
    ![Image](https://github.com/user-attachments/assets/ba3d8985-f6e1-4f44-9be5-750d057d174d)
    

## Scorecards & CPM Goal Tracking

![Image](https://github.com/user-attachments/assets/588caefb-1f01-4683-a42b-edbe480c46d1)

| Metric | Description |
| --- | --- |
| Total Spent | Total ad budget used during the selected time period and location |
| Total Mess | Total messaging conversations started. |
| Cost per Mess | Calculated as: `Total Spent / Total Mess`. This reflects how efficiently the campaign converts spend into conversations. |
| Campaign Mess | Messages generated from campaigns with the objective set to "Messages". |
| Engagement Mess | Messages generated from campaigns with the objective set to "Engagement". |

A Target CPMess is set at 25,000 VND. The Cost per Mess card is conditionally formatted:

- Green if it’s on track (≤ 25,000 VND)
- Red if it exceeds the target

## Time Series Visualizations

### 1. Daily Spent

![Screenshot 2025-05-03 at 3.34.17 pm.png](attachment:c43d64d6-3123-46ca-b7d4-f78e850b24cd:Screenshot_2025-05-03_at_3.34.17_pm.png)

- Daily ad spend ranged consistently between 1.5M to 2.0M VND, with occasional spikes (e.g. April 20 and 29 at 2.3M).
- On April 20, spending peaked above 2.3M VND, which also saw a high messaging volume, suggesting effective campaign execution that day.
- However, April 25 experienced a spike in spend without a proportional increase in messaging, indicating potential inefficiency or underperforming creatives.

### 2. Daily Messaging Conversations

![Screenshot 2025-05-03 at 3.39.00 pm.png](attachment:e1f1d541-3fed-4dca-a84d-c70b47879284:Screenshot_2025-05-03_at_3.39.00_pm.png)

- Messaging volume generally hovered between 70–100 conversations/day, showing a healthy and consistent user response.
- A noticeable drop occurred on April 24, where messaging dipped below 70, despite no significant change in spending.
- The strongest messaging performance was around April 19–21, aligning with efficient spend utilization.

### 3. Daily Cost per Message

![Screenshot 2025-05-03 at 3.44.05 pm.png](attachment:b9544a5b-d30c-46fb-b864-34d98ead54cd:Screenshot_2025-05-03_at_3.44.05_pm.png)

- Cost per message started at nearly 30,000 VND threshold on April 15, then gradually decreased to a more efficient range (~20,000 VND) between April 19–23.
- April 23 and 25 showed minor spikes, exceeding 25,000 VND, likely due to reduced engagement on those days.
- Despite some fluctuations, the overall trend remains below the target CPM (25,000 VND), which confirms strong cost efficiency across the campaign period.

## Campaign Performance

### Top 5 Inefficient Campaigns

![Screenshot 2025-05-03 at 3.48.50 pm.png](attachment:06308ddf-9081-42e1-928a-ad56021aec2f:Screenshot_2025-05-03_at_3.48.50_pm.png)

These campaigns had the highest cost per message, exceeding the CPMess target (25,000 VND) by over 100% in most cases.

⇒ These campaigns require urgent review; consider adjusting targeting, creatives, or frequency.

### **Top 5 Efficient Campaigns**

![Screenshot 2025-05-03 at 3.52.47 pm.png](attachment:890d2f8a-6e70-4aa7-bf55-d5bca584d876:Screenshot_2025-05-03_at_3.52.47_pm.png)

These campaigns generated messages at **the lowest cost**, staying well below 25,000 VND.

⇒ These campaigns are strong candidates for scaling or duplication.

### Top 5 Highest-Spend Campaigns

![Screenshot 2025-05-03 at 3.55.26 pm.png](attachment:281439ee-ab32-4cc0-a964-97a6733313c5:Screenshot_2025-05-03_at_3.55.26_pm.png)

These campaigns occupied the **largest share of the total ad budget**.

⇒ Monitor closely. High spend without matching efficiency may require reallocation.

### Top 5 Attractive Campaigns (by CTR)

These ads received **the most clicks per impression**, showing strong creative appeal and relevance.

![Screenshot 2025-05-03 at 3.57.04 pm.png](attachment:2d7aa746-189b-42bb-b599-a17841f06cea:Screenshot_2025-05-03_at_3.57.04_pm.png)

⇒ Repurpose or A/B test these ad creatives across other audiences.

### Top 5 Cost-Effective Click Campaigns (by CPC)

![Screenshot 2025-05-03 at 3.58.15 pm.png](attachment:67ab2490-53da-414b-8638-6ed4b896b850:Screenshot_2025-05-03_at_3.58.15_pm.png)

⇒ Consider pairing with retargeting.

# 4. Conclusion

This Facebook Ads campaign analysis project provided a comprehensive, data-driven evaluation of messaging performance across various campaigns, locations, and dates. By focusing on the key metric — Cost per Message with a defined target of 25,000 VND — the project successfully highlighted both high-performing and inefficient campaigns.

Through a structured workflow that began with raw data cleaning, aggregation (with location classification), and the creation of an interactive dashboard, the analysis empowered marketers to:

- Identify campaigns with optimal cost efficiency
- Track real-time performance through dynamic filters (Location & Date)
- Understand trends in daily spending, engagement, and cost per message
- Make informed decisions on budget allocation and creative optimization

In addition, the use of scorecards and time-series visualizations offered clear and immediate insights, while leaderboard tables categorized campaigns by CTR, CPC, and budget effectiveness, providing strategic direction for future ad planning.

Overall, the project not only meets the business goal of CPM optimization but also serves as a flexible tool for continuous performance monitoring and strategic ad investment.
