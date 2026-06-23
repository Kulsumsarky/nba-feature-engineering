# NBA Player Longevity Prediction - Feature Engineering

## Project Overview
This project engineers features from an NBA player performance 
dataset to predict whether a player will last 5+ years in the league.

## Dataset
- Size: 1,340 players, 22 features
- Target: target_5yrs (1=lasted 5+ years, 0=did not)
- Missing values: None

## Feature Engineering Workflow

### Step 1: Define Target Variable
- target_5yrs isolated as dependent variable
- 831 players lasted 5+ years, 509 did not

### Step 2: Drop Non-Predictive Columns
- Unnamed: 0 — index column, adds no value
- name — player name, causes data leakage

### Step 3: Correlation Analysis
- Built heatmap to identify redundant features
- Dropped highly correlated pairs (correlation > 0.95)

### Step 4: Dropped Redundant Features
- fgm, fga — redundant with pts (corr=0.99)
- oreb, dreb — redundant with reb (corr=0.98)
- fta — redundant with ftm (corr=0.98)
- 3pa — redundant with 3p_made (corr=0.98)

### Step 5: Engineer New Features
- pts_per_min — scoring efficiency per minute played
- efficiency — overall impact (pts+reb+ast+stl+blk-tov)

### Step 6: Handle Missing Values
- No missing values found after feature engineering

## Final Dataset
- Rows: 1,340
- Columns: 16
- Missing values: 0

## Key Features Kept
- gp, min, pts, fg, 3p_made, 3p
- ftm, ft, reb, ast, stl, blk, tov
- pts_per_min, efficiency (engineered)

## Environment Setup
pip install pandas numpy matplotlib seaborn

## Files
- nba_feature_engineering.ipynb - Main notebook
- nba_data.csv - Dataset
- ### Step 7: Feature Scaling
- Applied StandardScaler to all features
- All features now have mean=0 and std=1
- Ensures distance-based models treat all features equally
