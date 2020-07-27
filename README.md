# Spotify Analysis

### Goal

Apply Exploratory Data Analysis and Machine Learning to extract interesting information from a Spotify songs dataset.

### Dataset:

[Top Spotify songs from 2010-2019](https://www.kaggle.com/leonardopena/top-spotify-songs-from-20102019-by-year)

This is Kaggle dataset with Spotify top songs for each year of the 2010's decade.

Dataset columns: 

1. ID
2. title: Song's title
3. artist: Song's artist
4. top genre: the genre of the track
5. year: Song's year in the Billboard
6. bpm: Beats per Minute - The tempo of the song
7. nrgy: Energy - The energy of a song *(the higher the value, the more energtic the song)*
8. dnce: Danceability *(The higher the value, the easier it is to dance to this song.)*
9. dB: Loudness in decibels *(The higher the value, the louder the song)*
10. live: Liveness *(The higher the value, the more likely the song is a live recording)*
11. val: Valence *(The higher the value, the more positive mood for the song.)*
12. dur: Length - The duration of the song.
13. acous: Acousticness *(The higher the value the more acoustic the song is.)*
14. spch: Speechiness *(The higher the value the more spoken word the song contains.)*
15. pop: Popularity *(The higher the value the more popular the song is.)*


### Pre-processing

#### Creating and grouping by supergenre

The `top genre` column brings detailed genres that could be aggregated into a single `supergenre`, for instance: 

* `pop`, `barbadian pop`, `australian pop` and `acoustic pop` could be grouped as the `pop` supergenre;
* `hip hop`, `canadian hip hop`, `detroit hip hop` can be aggregated to `hip hop` supergenre.

This was done mostly looking at the last word of the `top genre` column, but some special cases where addressed, such as `hip hop`, and some highly representative genres were kept as their originals (`dance pop`, for instance).

Following this new labeling, 29 supergenres were found out of the 50 original genres.

#### Supergenre criteria for selection for training

A new dataset was generated as a subset of the original one with the condition of fulfilling the two following criteria.

1. Only supergenres with at least 5 songs are allowed. 16 of the 29 supergenres passed this criterion.
2. For genres with more than 15 songs, only 15 will be chosen randomly. The three genres that fell in this category were `dance pop`, `pop` and `canadian pop`.

After the described preprocessing, the original (603,15)-shape dataframe was transformed into a (173, 16)-shape dataframe.

Preprocessed file location: `data/002_intermediate_data/preprocessed_data.csv`

