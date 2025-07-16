# Metal Music Lyrical Sentiment Analysis and Data Profiling Pipeline

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Al-ba22/metal-lyrics-etl-pipeline/blob/main/notebooks/metal_lyrics_sentiment_analysis.ipynb)

## Project Overview

This project implements an end-to-end data pipeline focused on analyzing lyrical content within a large archive of metal songs. It demonstrates core data engineering practices, including data extraction, comprehensive cleaning, sentiment analysis, and essential data profiling. The goal is to derive insights into the emotional tone and key characteristics of metal lyrics.

## Technologies Used

* **Python:** The primary programming language.
* **Pandas:** For robust data manipulation, transformation, and aggregation.
* **TextBlob:** Used for performing sentiment polarity analysis on lyrical content.
* **Matplotlib:** For creating the overall sentiment distribution histogram.
* **KaggleHub:** Utilized for programmatic dataset acquisition.

## Dataset

The dataset analyzed is the "[Large Metal Lyrics Archive (228k Songs)](https://www.kaggle.com/datasets/markkorvin/large-metal-lyrics-archive-228k-songs)" by Mark Korvin, downloaded directly via KaggleHub. It contains lyrical data for over 228,000 metal songs, along with artist and album information.

## Data Access

### Sample Dataset (1,000 rows)
A lightweight sample is included in this repo:
`data/metal_lyrics_sample.csv`

### Full Cleaned Dataset (377MB)
Due to GitHub’s file size limits, the complete CSV is available on Google Drive:

[Download Full Dataset] (https://drive.google.com/file/d/1Eh_KI_0URGzKnTNHlDOHu2QIY4LdfxZT/view?usp=share_link)

## Key Features

This project pipeline includes the following stages and functionalities:

* **Data Extraction & Ingestion:** Programmatically downloads the extensive metal lyrics dataset from KaggleHub.
* **Robust Data Cleaning & Preprocessing:**
    * Removes punctuation and special characters from lyrics using regex.
    * Converts all lyrical text to lowercase for consistent analysis.
    * Filters out empty or excessively short lyric entries (less than 30 characters) to maintain data quality.
    * Strips excess whitespace from cleaned lyrics.
* **Sentiment Analysis:** Applies the TextBlob library to compute a polarity score for each song's lyrics, ranging from -1 (most negative) to +1 (most positive).
* **Overall Sentiment Visualization:** Generates and displays a **histogram** of the sentiment scores across all songs, providing a general understanding of the emotional landscape of metal lyrics.
* **Artist-Level Sentiment Profiling:**
    * Calculates the **average sentiment score for each artist**.
    * Identifies and **prints** the top 10 artists with the most negative and most positive average lyrical sentiments, offering insights into thematic leanings.
* **Data Export:** Saves the fully cleaned and sentiment-scored dataset to a CSV file (`metal_lyrics_cleaned.csv`), making it accessible for further analysis or integration into other data systems.

## How to Run This Project

This project is designed to be run in a Google Colab environment for ease of use and reproducibility.

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/Al-ba22/metal-lyrics-etl-pipeline.git](https://github.com/Al-ba22/metal-lyrics-etl-pipeline.git)
    cd metal-lyrics-etl-pipeline
    ```
    
2.  **Open in Google Colab:**
    * Navigate to the `metal_lyrics_sentiment_analysis.ipynb` file within the cloned repository on GitHub.
    * Click the "Open in Colab" button (usually found near the top right of the file preview).

3.  **Install Dependencies:**
    * Once the notebook is open in Colab, run the first few code cells to install necessary libraries (e.g., `!pip install kagglehub textblob`).

4.  **Execute All Cells:**
    * Run all the cells sequentially (`Runtime > Run all`) to execute the entire ETL pipeline, data cleaning, sentiment analysis, data profiling, and visualization steps.
    * The processed `.csv` file will be generated in your Colab environment, and the histogram plot will be displayed.

## Project Structure

* `metal_lyrics_sentiment_analysis.ipynb`: The main Google Colab notebook containing all the Python code for the ETL, analysis, and visualization.
* `metal_lyrics_cleaned.csv`: (Generated upon execution) The output CSV file containing the cleaned lyrics along with their calculated sentiment scores.
* `README.md`: This file, providing an overview of the project.

## Future Enhancements

* **Expanded Data Profiling:**
    * Analyze the distribution of songs per artist and per album to understand content contributions more broadly.
    * Investigate the correlation between song length and sentiment.
* **Advanced Text Analysis:** Incorporate stop word removal, stemming, or lemmatization for deeper linguistic insights.
* **Visualizations:** Create bar charts to visualize the top/bottom artists by sentiment, or other relevant aggregations.
* **Genre-Specific Analysis:** If a dataset with reliable metal sub-genre information becomes available, perform sentiment analysis grouped by genre.
* **Cloud Deployment:** Explore containerizing the pipeline using Docker and deploying it on a cloud platform (e.g., AWS S3/Glue/Lambda, GCP Cloud Functions/Dataflow) to demonstrate production readiness.
* **Error Handling & Logging:** Implement more robust error handling and comprehensive logging for production-grade reliability.
