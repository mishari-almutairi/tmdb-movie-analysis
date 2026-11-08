# TMDb Movie Revenue Analysis

An exploratory data analysis of the TMDb movie dataset for Udacity's **Investigate a Dataset** project. The notebook examines how movie revenue relates to budget, audience ratings, runtime, genre, and release period using pandas, NumPy, and Matplotlib.

## Research questions

1. How are adjusted movie budgets, audience ratings, and runtime associated with adjusted revenue?
2. How does adjusted revenue vary across genres and five-year release periods?

## Dataset and preparation

The included TMDb dataset contains **10,866 records and 21 columns**, covering releases from **1960 to 2015**. It is the movie dataset supplied for this Udacity project.

Preparation removes one fully duplicated row and creates a financial subset of **3,854 movies** with positive adjusted budgets and revenues. All exploratory comparisons use that subset. Financial figures use inflation-adjusted **2010 US dollars**.

## Main findings

- Adjusted budget has the strongest positive association with adjusted revenue among the three numerical characteristics examined: Spearman correlation **0.656**. Ratings (**0.240**) and runtime (**0.284**) have weaker positive associations.
- **Animation** has the highest median adjusted revenue, approximately **$205.73 million**, followed by Adventure (**$144.58 million**) and Family (**$130.66 million**).
- **1965-1969** has the highest median adjusted revenue among the release periods, approximately **$209.35 million**, based on just **36 movies**. Later periods do not show a consistent upward trend.

These are descriptive associations. They do not establish causation or statistical significance.

## Project files

| File | Purpose |
| --- | --- |
| [Investigate_a_Dataset.ipynb](Investigate_a_Dataset.ipynb) | Analysis, visualizations, conclusions, and limitations. |
| [Investigate_a_Dataset.html](Investigate_a_Dataset.html) | Saved HTML report; download and open in a browser. |
| [Database_TMDb_movie_data/tmdb-movies.csv](Database_TMDb_movie_data/tmdb-movies.csv) | Input dataset. |
| [requirements.txt](requirements.txt) | Python dependencies with versions from the local environment. |

## Run locally

The notebook uses a Windows-style relative dataset path. Run it on **Windows** from the repository root. Python **3.14** was used in the local environment.

```powershell
git clone https://github.com/mishari-almutairi/tmdb-movie-analysis.git
cd tmdb-movie-analysis
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
```

Open `Investigate_a_Dataset.ipynb` in a notebook editor, such as VS Code with its Jupyter extension, and select `.venv` as the Python kernel. Run the analysis cells from top to bottom. The final cell exports an HTML report and is optional.

For the browser-based Jupyter interface, install and launch it separately:

```powershell
.\.venv\Scripts\python.exe -m pip install notebook
.\.venv\Scripts\python.exe -m notebook
```

To export the saved notebook outputs without rerunning the analysis:

```powershell
.\.venv\Scripts\python.exe -m nbconvert --to html Investigate_a_Dataset.ipynb
```

On macOS or Linux, use the appropriate virtual-environment commands and change the CSV path in the loading cell to `Database_TMDb_movie_data/tmdb-movies.csv` before running the analysis.

## Limitations

- Requiring positive budgets and revenues may introduce selection bias. Movies with known positive revenue but a zero reported budget are also excluded.
- Genre groups overlap because movies can have multiple genres, and some groups have very small samples.
- Earlier release periods contain fewer movies. The final group covers only 2015, rather than a complete five-year period.
- Very small positive financial values were retained; their data quality remains uncertain.
- Relationships were examined separately, without controlling for other influences or performing statistical significance tests.

Possible extensions include comparing all movies with positive reported revenue and examining genre differences while accounting for budget.

## Acknowledgments

Completed as part of Udacity's Data Analyst coursework. The analysis uses the TMDb movie dataset provided with the project; the included dataset retains any applicable original terms.
