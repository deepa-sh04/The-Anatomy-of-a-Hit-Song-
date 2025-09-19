# Day 2 — 2025-09-20

**Goals for today**
- Clean and explore missing values
- Visualize feature correlations with a heatmap
- Split data into training and testing sets

**What I did**
- Used `df.isnull().sum()` and `df.describe()` to analyze missing data and get a statistical summary.
- Cleaned the `in_shazam_charts` column by filling missing values with zeros.
- Generated a correlation heatmap using `seaborn` to understand relationships between features.
- Separated features (X) and target (y).
- Split the dataset into 80% training data and 20% testing data using `train_test_split`.

**Errors & Fixes**
- No major errors today, as the data was successfully loaded in Day 1.

**What I learned**
- The importance of data cleaning and how to handle missing values.
- How to interpret a correlation heatmap to make informed decisions about feature selection.
- The fundamental concept of splitting data to prevent a model from overfitting.

```markdown
- Cleaned the `in_shazam_charts` column by filling missing values with zeros.

```python
# Before cleaning
print(df['in_shazam_charts'].isnull().sum())

# After cleaning
df['in_shazam_charts'] = df['in_shazam_charts'].fillna(0)
print(df['in_shazam_charts'].isnull().sum())
<img width="1187" height="584" alt="image" src="https://github.com/user-attachments/assets/07226741-5532-4d2a-b684-5e1c7375918b" />
```markdown
- Generated a correlation heatmap using `seaborn` to understand relationships between numeric features.

```python
import seaborn as sns
import matplotlib.pyplot as plt

# Create a list of the numerical features to analyze
numeric_features = [
    'artist_count', 'released_year', 'released_month', 'released_day',
    'in_spotify_playlists', 'in_spotify_charts', 'streams',
    'in_apple_playlists', 'in_apple_charts', 'in_deezer_playlists',
    'in_deezer_charts', 'in_shazam_charts', 'bpm', 'danceability_%',
    'valence_%', 'energy_%', 'acousticness_%', 'instrumentalness_%',
    'liveness_%', 'speechiness_%'
]

# Calculate the correlation matrix
corr_matrix = df[numeric_features].corr()

# Plot the heatmap
plt.figure(figsize=(15, 12))
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm', fmt=".2f")
plt.title('Correlation Matrix of Song Features')
plt.show()
<img width="813" height="691" alt="image" src="https://github.com/user-attachments/assets/18d9c4ac-2f5b-4575-9aeb-d7a7503219b1" />

