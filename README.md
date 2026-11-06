# 📺 Trending YouTube Analysis: Foundations of Computer Science Project

This repository contains the final project developed for the **Foundations of Computer Science** course (2025–26) as part of the MSc in Data Science at the **University of Milan-Bicocca (UNIMIB)**.

The project consists of a single **Jupyter notebook**: a series of 15 Python exercises on the **Trending YouTube** dataset, designed to build fluency with the language and with data manipulation using **pandas** and **NumPy**.

---

## 🎯 Project Objectives

* **Data Integration:** Building a single clean dataframe from 10 country-level files, handling duplicates, missing values and excluded records.
* **Feature Engineering:** Creating new variables such as a normalised `like_ratio`, 10-minute publish intervals and split trending dates.
* **Aggregation & Ranking:** Answering analytical questions about channels, tags, time intervals and countries through grouping and aggregation.
* **Multi-source Merging:** Combining video data with category metadata stored in separate JSON files.

---

## 📡 Dataset

The notebook works on the Trending YouTube dataset, which contains the daily trending videos for **10 countries**: Canada (CA), Germany (DE), France (FR), Great Britain (GB), India (IN), Japan (JP), South Korea (KR), Mexico (MX), Russia (RU) and the United States (US).

| File | Content |
|---|---|
| `<CC>videos.csv.zst` | Trending videos (title, channel, tags, views, likes, dislikes, publish time, trending date, flags for disabled comments/ratings...), compressed with Zstandard |
| `<CC>_category_id.json` | Mapping between category IDs and category names for that country |

> ⚠️ The data files are **not included** in this repository. They were provided with the course material and must be downloaded separately.

---

## 📝 Exercises

| # | Task |
|---|---|
| 1 | Build a single dataframe by concatenating all country files, adding a `country` column; remove duplicates and inspect missing values |
| 2 | Extract all videos with no tags |
| 3 | Compute the total number of views for each channel |
| 4 | Move videos with disabled comments *and* ratings, or flagged as errored/removed, into a separate `excluded` dataframe |
| 5 | Add a `like_ratio` column, normalised as likes / (likes + dislikes) to avoid `inf` and `NaN` values |
| 6 | Cluster the publish time into 10-minute intervals |
| 7 | For each interval, compute the number of videos and the average likes and dislikes |
| 8 | Count the number of videos for each tag (stored as a single `\|`-separated string) |
| 9 | Find the tags with the largest number of videos |
| 10 | For each (tag, country) pair, compute the average like ratio |
| 11 | For each (trending date, country) pair, find the video with the most views |
| 12 | Split the trending date into year, month and day columns |
| 13 | For each (month, country) pair, find the video with the most views |
| 14 | Read all the JSON files with the video categories |
| 15 | For each country, count how many videos have a non-assignable category |

---

## 🛠️ Techniques Covered

* **Data Loading:** Reading compressed (`.zst`) and JSON files into pandas.
* **Data Cleaning:** Handling duplicates, missing values and division-by-zero cases.
* **Combining Data:** `concat` and `merge` across dataframes.
* **Aggregation:** `groupby`, `agg` and `idxmax`.
* **String Processing:** Splitting multi-valued columns and using `explode`.
* **Date & Time:** `to_datetime`, `dt.floor` and `Timedelta`.
* **Core Python:** Dictionaries, loops and lambda functions.

---

## 📈 Key Insights

* The raw dataset contains **375,942 rows**; removing **12,570 duplicates** brings it to 363,372, and a further **2,438 excluded videos** (disabled comments and ratings, or errored/removed) leave **360,934** clean rows.
* **36,221 videos** have no tags at all.
* The raw likes/dislikes ratio produces **2,355 `inf`** and **4,619 `NaN`** values, which motivated the normalised `like_ratio`.
* **"funny"** (14,573 videos) and **"comedy"** (11,968) are the most frequent tags.
* **ChildishGambinoVEVO** leads in total views (~10.9 billion), followed by **Marvel Entertainment** (~10.1 billion).
* **944 videos** have a non-assignable category, with Russia (194), India and South Korea (159 each) leading, versus just 3 in Mexico.

---

## 📂 Repository Structure

* `Final_Project_FOCS.ipynb` — The complete notebook with all 15 exercises, from data loading to category merging.

---

## 📌 Notes

* Code comments and some variable names are a mix of English and Italian.
* Per the course rules, AI tools may be used provided their use is described in the notebook.

---

## 👥 Contributors
- [@ilaria-cesa](https://github.com/ilaria-cesa)
- [@mezza04](https://github.com/mezza04)

---
*Developed by Andrea Porro, Ilaria Cesaratto, and Chiara Mezzanica as part of the MSc in Data Science program at the **University of Milan-Bicocca (UNIMIB)**.*
