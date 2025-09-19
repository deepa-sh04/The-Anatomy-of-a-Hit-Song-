# Day 1 — 2025-09-19
**Goals for today**
- Setup environment (Anaconda, Jupyter)
- Download dataset: Popular_Spotify_Songs.csv
- Load data and inspect structure

**What I did**
- Installed Anaconda, set up Jupyter Notebook
- Acquired dataset from Kaggle, saved in `data/raw/`
- Wrote code in notebook to load CSV with pandas:

    ```python
    import pandas as pd
    df = pd.read_csv("Popular_Spotify_Songs.csv", encoding='latin1')
    df.info()
    ```
- Used `df.info()`, `df.head()` to inspect columns, data types, missing values

**Errors & Fixes**
- *FileNotFoundError*: script couldn’t find CSV — solved by placing file in project folder
- *UnicodeDecodeError*: solved by specifying `encoding='latin1'`

**What I learned**
- How `encoding` works; why many CSVs have issues
- Importance of correct file paths
- Getting familiar with the dataset: number of columns, missing values

<img width="905" height="688" alt="image" src="https://github.com/user-attachments/assets/93140d4a-68cb-4905-b4cb-1658e2eae6f0" />
