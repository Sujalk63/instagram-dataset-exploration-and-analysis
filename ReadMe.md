# Analysis on Fetched Instagram Profile and Content Data

GitHub Repo for Automated Scraping: [Instagram Profile and Content Scraping](https://github.com/Sujalk63/InstaContentScraper)

---

## Overview 📊

This repo analyzes **Instagram profile** and **content data** fetched using an **automation tool** I developed. It focuses on deriving insights into **content virality**, **engagement patterns**, and **niche popularity** to help content creators optimize their strategies.

This project will remain active and **continuously updated** with new insights 📊 as more data is collected.

## Purpose 🎯

- **Focus**: Viral trends 🔥, best posting times 🕒, niche analysis 📈 and more.
- **Goal**: Provide actionable insights for content optimization 📌 through detailed data analysis.

## 📥 Data Source

- The data used in this analysis is automatically fetched from Instagram profiles via custom-built automation scripts 📡. The data collection is ongoing, with plans for future expansion 🌱. You can access the automation tool and data fetching scripts on my GitHub for reference and further use 💻.
- _GitHub Repo:_ [Instagram Profile and Content Scraping](https://github.com/Sujalk63/InstaContentScraper)
- _Soon available on Kaggle._

### Example:

Instead of considering accounts with 50 followers or 50M followers, we analyze those between **~2K and ~2.5M** — covering 80–90% of real creators.

## 1) Top 15 Trending Professions 🔥

In this analysis, I explored the relationship between **Instagram professional labels** 💼 and **mean follower counts** 📊.

### Key Insights 💡:

- **Comedian & Creative Director**: Average followers ~700K 🎭, steady but not extreme growth.
- **Gaming Video Creator**: Leading with **5.8M followers** 🎮, great for high engagement & reach.
- **Media, Actor, Scientist**: Followers range from **2M - 3M** 📊, offering broad audience potential.

### Code link: [ProfessionalLabelsVsFollowerCount](./1_ProfessionalLabelsVsFollowerCount.ipynb)

### Visual Representation:

![Follower Count Analysis](/images/ProfessionalLabelsVsFollowerCount.png)

## 2) 📉 From Misleading to Meaningful: Why Filtering Followers Matters

Earlier insights may be misleading because raw follower counts include **extremes** — from brand new accounts with just a few followers to celebrities with tens of millions. These **outliers** skew averages and paint a distorted picture of what's typical..

### Solution

- **We use statistical bounds (IQR method)** to remove extreme cases and focus on the **core audience** (where most users fall).
- **Lower Bound**: Ensures we avoid users with unrealistic low counts (e.g., 0–10 followers).
- **Upper Bound**: Helps us exclude a few superstars (celebs) with 10M+ followers that skew averages heavily.
- This keeps our insights accurate, especially when analyzing **engagement, domain performance, and content effectiveness**.

```python

df = df.dropna(subset=["Followers Count"])

q1 = df["Followers Count"].quantile(0.10) # 10% of users have followers ≤ this value
q3 = df["Followers Count"].quantile(0.90) # 90% of users have followers ≤ this value

iqr = q3 - q1 # Getting where the 80% usernames are!!

lower_bound = q1
upper_bound = q3

filtered_df = df[(df["Followers Count"] >= lower_bound) & (df["Followers Count"] <= upper_bound)]

```

### Code link: [OutliersRemoved](./2_OutliersRemoved.ipynb)

### Visual Representation:

![Outliers removed & Follower Count Analysis](/images/2_OutliersRemoved.png)

## 👤 Author & Contact

**Sujal Karmakar**  
📧 Email: [sujalkarmakar6363@gmail.com](mailto:sujalkarmakar6363@gmail.com)

_Contributions, suggestions, and feedback are heartily welcomed!_ 🤝  
Let's build something insightful together.
