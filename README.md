# Album Recommender System

An end-to-end data science project exploring personalised album recommendations using ListenBrainz listening history data.

## Project aim
To build a recommendation system that suggests albums based on a user's listening behaviour, with an initial focus on implicit feedback collaborative filtering.

## Project motivation
Most music recommendation systems focus heavily on individual tracks and playlists. I wanted to approach music discovery at the album level, using listening history to understand which albums users engage with and identify patterns of overlap between listeners.

This project also provides an opportunity to develop an end-to-end recommendation workflow, from processing large raw datasets through to modelling, evaluation and eventually deployment.

## Data
The project currently uses a ListenBrainz listens dump containing approximately 5 million listening records.

Each raw record contains information including:

- user ID
- track name
- artist name
- release name

The raw dataset is stored as JSON Lines and is not included in this repository due to its size.

For the initial analysis, an album is represented using a combination of:

artist_name + release_name

For example:

charli xcx — brat

This is currently a provisional album identifier.

## Current progress
- [x] Inspect raw ListenBrainz data
- [x] Assess collaborative-filtering viability
- [x] Build modelling dataset
- [x] Build SQL analytics database

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
│
└── data/
    └── README.md
```
