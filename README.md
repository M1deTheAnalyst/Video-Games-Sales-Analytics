# Video Game Sales Analytics Dashboard

> A Power BI dashboard that identifies top games, key markets, and platform performance driving overall sales across consoles, regions, publishers, and time periods.

<img width="1489" height="867" alt="Video Games Sales Dashboard" src="https://github.com/user-attachments/assets/1e3343fd-858c-4453-b24f-4bde478643f0" />

---

## 📋 Table of Contents

- [Overview](#overview)
- [Dashboard Pages](#dashboard-pages)
  - [Video Game Sales Analytics](#1-video-game-sales-analytics)
- [Key Metrics & KPIs](#key-metrics--kpis)
- [Relationship Model](#relationship-model)
- [Dataset Schema](#dataset-schema)
- [File Structure](#file-structure)
- [Getting Started](#getting-started)
- [Prerequisites](#prerequisites)
- [Usage & Filters](#usage--filters)
- [Insights Summary](#insights-summary)

---

## Overview

The **Video Game Sales Analytics Dashboard** is a Power BI report built to analyse global video game sales performance across titles, consoles, publishers, regions, and time periods. It enables game publishers, market analysts, and business strategists to identify top-performing titles, understand which platforms and regions drive revenue, and explore how critic scores correlate with commercial success.

### 🎯 Business Objectives

- Identify the top-grossing game titles and the consoles that drive their revenue
- Determine which geographic region contributes the most to overall global sales
- Track how game release volume by month translates into revenue across the calendar year
- Evaluate whether higher critic scores reliably predict stronger average sales per title
- Rank publishers and their associated developers by total sales contribution
- Benchmark console platform performance to guide platform-first release strategy

---

## Dashboard Pages

### 1. Video Game Sales Analytics

> *Surfaces the top game, top region, and top console while breaking down sales by title, console, publisher, month, critic score band, and geography.*

<img width="1489" height="867" alt="Video Games Sales Dashboard" src="https://github.com/user-attachments/assets/7360a04f-b1e5-45de-b3a2-054000a302da" />

#### KPI / Slicer Filters

| Filter | Options |
|--------|---------|
| **Year** | All years in dataset |
| **Genre** | All 20 game genres |

#### KPI Cards

| Card | Value | Supporting Detail |
|------|-------|------------------|
| **Top Game** | Call of Duty: Black Ops II | 1.9% contribution to overall sales ($29.6) — Publisher: Activision, Developer: Treyarch |
| **Top Region** | NA (North America) | 43.0% contribution ($673.4) — Most played game: Call of Duty: Ghosts |
| **Top Console** | PC | 2.6% contribution ($40.2) — Most played game: The Sims 4 |

#### Visuals

**Total Sales and Total Games by Month : Combo Chart (Bar + Line)**
- Tracks monthly total sales revenue (bar) against total number of game releases (dotted line) across the calendar year
- Annotated with month-over-month percentage changes to quickly identify growth and decline periods
- Useful for spotting seasonal spikes, holiday-window patterns, and release drought periods

**Avg Sales Per Game by Critic Score Band : Horizontal Bar Chart**
- Groups all titles into six critic score tiers and compares the average sales generated per game within each band
- Answers the core question: do higher-rated games actually sell more?
- Supports data-driven decisions around marketing investment for high-scoring titles

**Total Sales by Title : Donut Chart** *(Drill-down to Console)*
- Displays proportional revenue share across the top-grossing game titles globally
- Drill-down reveals which specific consoles each title generated its revenue on
- Provides a quick view of franchise dominance within the overall market

**Total Sales by Region : Clustered Bar Chart**
- Ranks the four major geographic markets (NA, PAL, JP, OTHER) by total sales contribution
- Enables regional prioritisation for launch strategies and localisation investment decisions

**Total Sales by Console : Horizontal Bar Chart** *(Drill-down to Title)*
- Ranks all console platforms by total aggregated sales
- Drill-down reveals which individual game titles power each console's revenue performance

**Total Sales by Publisher : Horizontal Bar Chart** *(Drill-down to Developer)*
- Ranks publishing companies by total global sales revenue
- Drill-down surfaces the specific development studios responsible for each publisher's commercial output

---

## Key Metrics & KPIs

| KPI | Definition |
|-----|-----------|
| **Top Game** | Title with the highest total global sales contribution |
| **Top Region** | Geographic market contributing the greatest share of total sales |
| **Top Console** | Platform with the highest total sales contribution |
| **Total Sales** | Aggregated global sales revenue across all titles (in millions USD) |
| **Avg Sales Per Game** | Mean sales value per distinct title within a given segment |
| **NA / PAL / JP / Other Sales** | Regional sales breakdowns for North America, Europe-Australia, Japan, and rest of world |
| **Critic Score Band** | Grouping of titles by Metacritic score tier (Poor → Excellent) |
| **Contribution to Overall Sales** | A title's, region's, or console's share of total dataset revenue expressed as a percentage |
| **Most Played Game (Region / Console)** | The title with the highest sales within a specific region or platform |

---

## Relationship Model

| From (FK) | To (PK) | Join Column |
|-----------|---------|-------------|
| fact_video_games_sales.release_date | date_table.Date | Date |

---

## Dataset Schema

| Column | Type | Description |
|--------|------|-------------|
| `S/N` | Integer | Serial number / unique row identifier |
| `title` | String | Game title name |
| `console` | String | Platform the game was released on (PS4, XBox One, PC, etc.) |
| `genre` | String | Game genre (Action, Shooter, Sports, RPG, etc.) |
| `publisher` | String | Publishing company responsible for the release |
| `developer` | String | Studio that developed the game |
| `critic_score` | Numeric | Metacritic critic score on a 0–10 scale |
| `total_sales` | Numeric | Global total sales in USD |
| `na_sales` | Numeric | North America regional sales (USD) |
| `jp_sales` | Numeric | Japan regional sales (USD) |
| `pal_sales` | Numeric | PAL region sales — Europe, Australia (USD) |
| `other_sales` | Numeric | Rest-of-world sales (USD) |
| `release_date` | Date | Date the game was officially released |
| `last_update` | Date | Date the record was last updated in the dataset |
| `Date` | Date | Full date key used to join the fact table to the date dimension |
| `Year` | Integer | Year dimension for period filtering |
| `Quarter` | String | Quarter label (Q1–Q4) for quarterly aggregations |
| `Month` | String | Month name for trend analysis |
| `Month Number` | Integer | Numeric month (1–12) for correct chronological sorting |

---

## File Structure

```
video-game-sales-dashboard/
│
├── 📊 Video_Games_Sales_Dashboard.pbix     # Main Power BI file
│
├── 📁 screenshots/
│   └── Video_Games_Sales_Dashboard.png
│
├── 📂 Video_Games_Sales_Dataset.xlsx       # Source data (fact table + date table)
│
└── 📄 README.md                            # This file
```

---

## Getting Started

### Prerequisites

| Tool | Version | Purpose |
|------|---------|---------|
| [Power BI Desktop](https://powerbi.microsoft.com/desktop/) | Latest | Open & edit `.pbix` |
| Microsoft Excel | 2016+ | View/edit source dataset (if applicable) |

### Installation & Setup

1. **Clone or download the repository**
   ```bash
   https://github.com/M1deTheAnalyst/Video-Games-Sales-Analytics.git
   ```

2. **Open the dashboard**
   - Launch **Power BI Desktop**
   - Go to `File → Open` and select `Video_Games_Sales_Dashboard.pbix`

3. **Verify data source connection**
   - Navigate to `Home → Transform Data → Data Source Settings`
   - Update the path to `Video_Games_Sales_Dataset.xlsx` if prompted
   - Click `Close & Apply` to confirm

4. **Refresh data**
   ```
   Home → Refresh
   ```

---

## Usage & Filters

The dashboard includes slicers supporting the following filters:

- 📅 **Year** : Filter all visuals to a specific release year
- 🎮 **Genre** : Isolate performance by game genre (Action, Shooter, Sports, RPG, and 16 more)

### Drill-Down Interactions

Several visuals support drill-down for deeper analysis:

| Visual | Primary Level | Drill-Down Level |
|--------|--------------|-----------------|
| Total Sales by Title | Game Title | Console |
| Total Sales by Console | Console Platform | Game Title |
| Total Sales by Publisher | Publisher | Developer |

---

## Insights Summary

1. **North America is the dominant revenue market** : NA contributes **43.0% ($673.4)** of all global video game sales — nearly equal to PAL and JP combined. Any publisher prioritising global revenue should treat NA as their primary launch market.

2. **PS4 is the top-performing console by a wide margin** : PS4 generates **$511.96** in total sales, more than double the XBox One ($257.9) and over twice the PS3 ($243). Sony's platform commanded the market during the dataset period, making it the most critical platform for multi-title publishers.

3. **Activision leads all publishers** : With **$230.38** in total sales and $53.75 ahead of second-place Ubisoft, Activision's dominance is driven almost entirely by the Call of Duty franchise, with Treyarch as its highest-grossing development studio.

4. **Critic scores are a strong predictor of commercial performance** : Games rated Excellent (9–10) average **$1.30** per title versus just **$0.13** for Poor-rated titles with a **10× difference**. Titles rated Very Good (8–8.9) still outperform Good-rated titles (7–7.9) by nearly **2×**, validating the commercial value of review quality.

5. **November is the most commercially powerful month** : Total game sales peak in November at **28.9% above average**, consistent with the holiday season release window adopted across the industry. Publishers launching flagship titles outside of Q4 face a structurally lower revenue ceiling.

6. **The top 5 titles are all multi-platform shooter or action franchises** : Call of Duty: Black Ops II, Call of Duty: Ghosts, Grand Theft Auto V, Call of Duty: Black Ops 3, and Minecraft collectively dominate the leaderboard confirming that franchise IP in the Shooter and Action genres holds a structural commercial advantage over new IP.

7. **July is the lowest revenue month of the year** : July records a **-52.8% drop** in total game sales, marking it as the industry's peak dry period. Publishers avoiding July for major releases are making commercially rational decisions based on audience purchasing behaviour.

---

## Author

**M1deTheAnalyst**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/m1detheanalyst)
[![GitHub](https://img.shields.io/badge/GitHub-Profile-181717?style=for-the-badge&logo=github)](https://github.com/M1deTheAnalyst)
[![X](https://img.shields.io/badge/X-Folllow-000000?style=for-the-badge&logo=twitter&logoColor=white)](https://x.com/M1deTheAnalyst)

---

*Built with ❤️ using Power BI | Data-driven decisions for the global gaming industry*
