# Data

The raw data used in this project comes from ListenBrainz and contains approximately **5 million listening records**, spanning from 13th February 2005 to 27th July 2026.

The data is stored locally and is not included in this GitHub repository because of its size.

This contains listening-history records in JSON Lines format.

As the project develops, cleaned or processed datasets may also be created from the raw ListenBrainz data.


## Local file structure

The notebook expects the raw ListenBrainz file to be stored locally at:

```text
data/2026/7.listens
```

The file is accessed in the notebook using:

listens_path = Path("..") / ".." / "data" / "2026" / "7.listens"
