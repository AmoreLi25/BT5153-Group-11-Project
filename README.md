# BT5153-Group-11-Project
YouTube Trending Video Comments Analysis Project

## Overview
This project aims to analyze YouTube comments and videos from the GB and US regions. We combine traditional sentiment analysis models (VADER, BERT) with engagement metrics to compute creator influence and performance scores. Furthermore, a large language model (LLM) application design is proposed, and a domain-specific analysis focusing on the cosmetics industry is conducted.
Please find the original datasets in "data.7z" file, and code in "BT5153Group11Project.ipynb" file.

## 1. Data Preprocessing
Environment Setup:Imported libraries: pandas, numpy, re, os, matplotlib, seaborn, transformers, datasets.

Data Loading:Loaded UScomments.csv, USvideos.csv, GBcomments.csv, GBvideos.csv into pandas DataFrames.

Missing Value Handling:Dropped null comment text rows.  Checked and cleaned missing values in video datasets.

Date Formatting:Converted date columns to standard datetime format.

Dataset Merging:Merged video datasets with corresponding comment datasets based on video_id. 

Engineering additional fields such as comment_length, comment_likes, like_rate_video, comment_rate.


## 2. Sentiment Analysis
VADER Sentiment Analysis:
Installed and applied vaderSentiment library.
Classified each comment into positive, neutral, or negative.
Aggregated sentiment distributions for overall GB comments and each video category.

  BERT Sentiment Analysis:
Loaded pretrained model cardiffnlp/twitter-roberta-base-sentiment.
Classified comments and mapped results to positive, neutral, negative.
Recalculated sentiment distributions at overall and category levels.


## 3. Influence Scoring
Feature Engineering: Calculated normalized engagement metrics.

Influence Score Calculation:
Computed influencer scores by weighted sum:
Influence Score=0.3×views+0.3×likes+0.2×comments+0.2×engagement rate


## 4. Performance Scoring
Sentiment Score Calculation:
Calculated sentiment score as:
Sentiment Score=(positive−negative)/(positive+neutral+negative)

Normalization: Normalized sentiment scores between 0 and 1.

Performance Score Calculation: Combined influence score and normalized sentiment score:
Performance Score=0.6×Influence Score+0.4×Normalized Sentiment Score


## 5. Dual Metric Design
Overall Metric Strategy:
Built a dual evaluation system combining:
Engagement-driven influence (quantitative metric).
Audience perception (sentiment-driven metric).

Ranking and Segmentation:
Ranked creators based on combined performance scores.
Identified top-performing creators across categories.


## 6. LLM Application Design
Objective:
Designed a concept to use large language models (LLMs) like GPT for future automated content sentiment monitoring.

Proposed Features:
Real-time sentiment evaluation for new videos.
Fine-grained detection of nuanced emotional reactions (e.g., sarcasm, irony).
Industry-specific tuning (e.g., cosmetics, technology).


## 7. Cosmetics Industry Specific Analysis
Subsetting Data:
Filtered videos and comments related to the cosmetics industry based on tags and channel information.

Industry Sentiment Trends:
Conducted targeted sentiment analysis using both VADER and BERT.
Observed particularly high positive sentiment around product reviews and beauty tutorials.

Insights:
Identified that cosmetics-related content tends to generate high engagement and predominantly positive emotional reactions.
Suggested opportunities for brands to leverage positive audience sentiment through targeted influencer collaborations.


## Notes
All models were executed with GPU acceleration where possible.
Data visualizations were generated using matplotlib and seaborn.
For confidential purpose, please replace null api with your api key.
