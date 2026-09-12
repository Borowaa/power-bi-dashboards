# Steam Market Dashboard (Power BI)

A one-page Power BI report on the Steam game market, built on a snapshot of **89,618 Steam games from March 2025**.
The report itself is in Polish.

## What the report shows

- **Headline figures** — total number of games, total number of user reviews, share of positive reviews
  and a review-weighted positive share.
- **Release trend** — number of Steam apps released per year.
- **Genres** — number of games in the five largest genres.
- **Studios** — top 10 studios by average success index, next to the number of games each has released.
- **Tags** — the most common game tags.
- **Platforms** — share of games supporting Windows, macOS and Linux.
- **Filters** — price range (USD), user review category and individual game.

## Data model

| Table | Role |
|---|---|
| `FACT_Games` | One row per game: price, release date, reviews, playtime and calculated measures |
| `DIM_Genres`, `BRIDGE_GameGenres` | Genres, with a bridge table because one game can belong to many genres |
| `DIM_Studio` | Developer studios |
| `FACT_GamesOS` | Supported operating systems per game |
| Tag table | Game tags split out of the source data |

Main measures: **Total Games**, **Total Reviews**, **Positive Review Rate**, **Weighted % Positive**
and **Avg Success Index**, plus calculated price ranges and review categories used by the filters.

## Data

`data/games_march2025_cleaned.csv` — a cleaned version of a public Steam games dataset (March 2025 snapshot):
89,618 games and 47 columns, including price, release date, genres, tags, developers, publishers, supported
platforms, positive and negative reviews, estimated owners and playtime.

The file is about 470 MB and is stored with Git LFS.

## Opening the report

Requirements: Windows and **Power BI Desktop** (free, available from the Microsoft Store).

**Just viewing:** download `dashboards/Projekt-na-podstawie-rynku-steam-Mateusz-Borowczak.pbix` from GitHub
(*Download raw file*) and open it in Power BI Desktop. The data is already imported into the report,
so the CSV is not needed.

**Refreshing the data:** clone the repository with Git LFS, then point the report at the CSV.

```bash
git lfs install
git clone https://github.com/Borowaa/power-bi-dashboards.git
```

In Power BI Desktop: *Transform data → Data source settings → Change Source*, and select
`data/games_march2025_cleaned.csv`.

## Repository structure

```
dashboards/   Power BI report (.pbix)
data/         Cleaned source dataset (CSV, Git LFS)
```

## Author

Mateusz Borowczak — [GitHub](https://github.com/Borowaa) · [LinkedIn](https://www.linkedin.com/in/mateusz-borowczak)
