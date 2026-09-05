# Spotify-Top-Songs-Analysis
Mini EDA project exploring what differentiates popular vs less popular artists on YouTube/Spotify-like data, focusing on streams, audio features, and licensing.
# Spotify/YouTube Tracks EDA – Mini Data Science Project

A small exploratory data analysis (EDA) project to test interest in a data science career.  
Using a cleaned track-level dataset, I ask simple but meaningful questions about artist popularity, audio features, and licensing, then answer them with basic statistics and visualizations.

## Data

- File: `Cleaned_spotify.csv (1)`
- Each row: one track
- Key columns:
  - `Artist`, `Track`, `Album`, `Channel`
  - Audio features: `Danceability`, `Energy`, `Loudness`, `Speechiness`, `Acousticness`, `Instrumentalness`, `Liveness`, `Valence`, `Tempo`, `Duration_min`
  - Engagement: `Views`, `Likes`, `Comments`, `Stream`
  - Metadata: `Album_type`, `Licensed`, `official_video`, `most_playedon`

The dataset combines audio characteristics with popularity metrics, making it suitable for simple EDA on what differentiates more and less successful artists.

## Questions

1. **Who are the most listened‑to artists vs less listened‑to artists?**  
2. **What makes less‑listened‑to artists different from the biggest ones?**  
   (Do audio features or metadata systematically differ?)  
3. **Between licensed and unlicensed artists, which ones get more streams?**

## Methods

- Tools: Python, pandas, matplotlib, seaborn, Jupyter notebook in VS Code  
- Main steps:
  - Load and inspect data
  - Create `log_Stream = log(1 + Stream)` to handle skewed stream counts
  - Define “big” vs “small” artists based on median total streams
  - Compare groups using:
    - Summary statistics (`groupby`, `describe`)
    - Visualizations (bar plots, boxplots, scatter plots, heatmaps)

No machine learning models or deployment; this is purely exploratory.

## Key Findings

### Q1 – Most vs least listened‑to artists

- A small number of artists account for a **large share of total streams**.  
- The distribution of streams per artist is **highly skewed**: many artists have low total streams, while a few dominate.  
- The same pattern appears in **average streams per track**.

### Q2 – Differences between big and small artists

- **Audio features** (e.g., `Danceability`, `Valence`, `Tempo`) are **broadly similar** between big and small artists.  
- Some modest differences appear in features like `Energy` and `Loudness`, but they are not dramatic.  
- Bigger differences show up in **metadata**:
  - Big artists are more likely to have an **official video**.  
  - Their tracks are concentrated on a few large **channels**.  
- This suggests that **visibility and distribution** matter more than raw audio features in explaining popularity gaps.

### Q3 – Licensed vs unlicensed artists

- **Licensed tracks** have higher average and median streams than unlicensed tracks.  
- The pattern generally holds within both big and small artists, though the gap may vary.  
- Being licensed (and the associated promotion/platform support) is strongly associated with higher streams.

## What Was Surprising or Boring

**Surprising:**
- Audio features alone do **not** differ dramatically between big and small artists.  
- **Licensing** and having an **official video** stand out as strong markers of higher streams.

**Boring / Limiting:**
- The analysis is **descriptive**: it shows associations, not causation.  
- High‑cardinality columns (`Artist`, `Channel`) make detailed per‑entity analysis repetitive unless focusing on a subset.

## What I’d Do Next

If I continued this project:

- Build a **simple predictive model** for `log(Stream)` using audio features + metadata.  
- Analyze the role of **channel size** and, if available, **time trends**.  
- Compare subsets (e.g., by genre or region) to see if patterns hold.  
- Refine the “big vs small” artist definition and explore more advanced visualizations.

## How to Run

1. Ensure you have Python 3.9+ installed.
2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn jupyter
   ```
3. Open `spotify_eda.ipynb` in VS Code (with the Python and Jupyter extensions) or in Jupyter.
4. Run cells from top to bottom.

## License

This is a learning project. The notebook and report are provided as-is for educational purposes.
