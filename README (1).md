# 🎬 Movie Recommendation System

A **content-based movie recommendation system** built using the TMDB 5000 dataset. Select any movie and get 5 personalized recommendations — complete with posters fetched live from the TMDB API — through a clean Streamlit web interface.

---

## 📸 Screenshot

> *(Add a screenshot of your app here)*

---

## 🧠 How It Works

This is a **content-based filtering** system. It recommends movies by analyzing the similarity between movie metadata rather than relying on user ratings.

**Pipeline:**

1. **Data Merging** — Two TMDB datasets (movies + credits) are merged on the `title` column
2. **Feature Engineering** — A unified `tags` column is created by combining:
   - Movie overview
   - Genres
   - Keywords
   - Top 4 cast members
   - Crew names
3. **NLP Preprocessing** — Text is cleaned using Porter Stemming and lowercased for normalization
4. **Vectorization** — Tags are converted to vectors using `CountVectorizer` (top 5000 features, English stop words removed)
5. **Similarity Computation** — Cosine similarity is computed across all ~4800 movies to find the closest matches
6. **Poster Fetching** — Movie posters are fetched in real-time from the TMDB API

---

## 🗂️ Project Structure

```
movie-recommender-system/
│
├── Movie-Recommender-System.ipynb   # Data preprocessing, vectorization & model building
├── app.py                           # Streamlit web application
├── movie_dict.pkl                   # Serialized movie dataframe (dictionary format)
├── movies.pkl                       # Serialized movies list
├── similarity.pkl                   # Precomputed cosine similarity matrix
├── requirements.txt                 # Python dependencies
├── Procfile                         # Heroku deployment config
└── setup.sh                         # Streamlit server config for Heroku
```

---

## 🛠️ Tech Stack

| Category | Tools |
|---|---|
| Language | Python 3 |
| Data Processing | Pandas, NumPy |
| NLP | NLTK (Porter Stemmer), Scikit-learn (CountVectorizer) |
| ML / Similarity | Scikit-learn (Cosine Similarity) |
| Web App | Streamlit |
| API | TMDB API |
| Deployment | Heroku |

---

## ⚙️ Getting Started

### Prerequisites

- Python 3.8+
- A free [TMDB API key](https://www.themoviedb.org/settings/api)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/your-username/movie-recommender-system.git
cd movie-recommender-system

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run the app
streamlit run app.py
```

> **Note:** The `movie_dict.pkl` and `similarity.pkl` files are required. Run the Jupyter notebook first to generate them if they are not present.

---

## 📓 Running the Notebook

To regenerate the model files from scratch:

1. Download the TMDB 5000 dataset:
   - [`tmdb_5000_movies.csv`](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)
   - `tmdb_5000_credits.csv`
2. Place both files in the project root
3. Run `Movie-Recommender-System.ipynb` end to end
4. This will generate `movie_dict.pkl` and `similarity.pkl`

---

## 🌐 Deploying on Heroku *(optional)*

The project is pre-configured for Heroku deployment with `Procfile` and `setup.sh`.

```bash
heroku login
heroku create your-app-name
git push heroku main
```

---

## 📊 Dataset

- **Source:** [TMDB 5000 Movie Dataset on Kaggle](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)
- **Size:** ~4800 movies
- **Features used:** `title`, `overview`, `genres`, `keywords`, `cast`, `crew`

---

## 🙋‍♀️ Author

**Your Name**  
[GitHub](https://github.com/your-username) · [LinkedIn](https://linkedin.com/in/your-profile)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
