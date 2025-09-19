# Day 2 — 2025-09-20

## 🎯 Goals
- Clean and explore missing values
- Visualize feature correlations with a heatmap
- Split data into training and testing sets

## ✅ What I Did
- Used `df.isnull().sum()` and `df.describe()` to inspect missing data.
- Filled missing values in the `in_shazam_charts` column with zeros.
- Generated a correlation heatmap with `seaborn`.
- Separated features (`X`) and target (`y`), then split into 80 % training / 20 % testing.

## 🐞 Errors & Fixes
- No major errors. Data loaded successfully from Day 1.

## 📚 What I Learned
- Handling missing values is crucial before modeling.
- How to read a correlation heatmap for feature selection.
- Why train/test splitting prevents overfitting.

## 💻 Code
```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Check and fill missing values
print("Missing values before cleaning:")
print(df['in_shazam_charts'].isnull().sum())

df['in_shazam_charts'] = df['in_shazam_charts'].fillna(0)

print("\nMissing values after cleaning:")
print(df['in_shazam_charts'].isnull().sum())

numeric_features = [
    'artist_count','released_year','released_month','released_day',
    'in_spotify_playlists','in_spotify_charts','streams',
    'in_apple_playlists','in_apple_charts','in_deezer_playlists',
    'in_deezer_charts','in_shazam_charts','bpm','danceability_%',
    'valence_%','energy_%','acousticness_%','instrumentalness_%',
    'liveness_%','speechiness_%'
]

corr_matrix = df[numeric_features].corr()

plt.figure(figsize=(15, 12))
sns.heatmap(corr_matrix, annot=True, cmap="coolwarm", fmt=".2f")
plt.title("Correlation Matrix of Song Features", fontsize=16)
plt.tight_layout()
plt.show()
