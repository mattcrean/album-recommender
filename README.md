# Album Recommender System

An end-to-end data science project exploring personalised album recommendations using ListenBrainz listening history data.

## Project aim
To build a recommendation system that suggests albums based on a user's listening behaviour, with an initial focus on implicit feedback collaborative filtering.

## Project motivation
Most music recommendation systems focus heavily on individual tracks and playlists. I wanted to approach music discovery at the album level, using listening history to understand which albums users engage with and identify patterns of overlap between listeners.

This project also provides an opportunity to develop an end-to-end recommendation workflow, from processing large raw datasets through to modelling, evaluation and eventually deployment.

## Data

The project uses a ListenBrainz listens dump containing approximately 5 million listening records.

Each raw record is stored in JSON Lines format and includes information such as:

- user ID
- track name
- artist name
- release name
- listening timestamp

The raw dataset is not included in this repository due to its size.

For the current modelling pipeline, an album-level interaction is defined using a combination of:

`artist_name + release_name`

For example:

`charli xcx — brat`

This remains a provisional album identifier, as the ListenBrainz `release_name` field can include singles, remixes and other release types as well as conventional albums.

The raw listening data is aggregated into unique user-album interactions, with `listen_count` representing the number of listens associated with each user-album pair.

To create a more suitable dataset for collaborative filtering, interactions are filtered iteratively so that:

- each remaining user has interacted with at least 5 albums
- each remaining album is associated with at least 2 users
- users with more than 2,000 distinct album interactions are excluded as an extreme upper tail

The final processed dataset contains:

- 9,858 users
- 42,567 albums
- 204,213 user-album interactions

This processed interaction dataset is saved locally in Parquet format and is used both for the SQLite analytics database and for subsequent recommendation modelling.

## SQL database

The cleaned interaction data is also structured into a local SQLite database for exploratory analysis.

The database contains separate tables for:

- users
- artists
- albums
- user-album interactions

A set of SQL queries in `sql/activity_queries.sql` is used to analyse:

- the most active users
- the most listened-to releases
- artist-level listening activity
- albums with the broadest listener overlap

The SQLite database itself is generated locally and is not included in the repository.

## Current progress
- [x] Inspect raw ListenBrainz data
- [x] Assess collaborative-filtering viability
- [x] Build and validate filtered modelling dataset
- [x] Build SQLite analytics database
- [x] Query user, artist and release activity using SQL
- [ ] Build recommendation baseline
- [ ] Develop collaborative filtering model
- [ ] Evaluate recommendations using ranking metrics

## Repository structure

```text
album-recommender/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── notebooks/
│   └── 01_inspect_data.ipynb
│   └── 02_build_dataset.ipynb
│   └── 03_build_sql_database.ipynb
|
├── sql/
│   └── activity_queries.sql
│
└── data/
    └── README.md
```
