
# Spotify Dataset Documentation

## Introduction

This documentation provides an overview of the Spotify dataset and the SQL queries used for data preparation. The dataset includes information about various tracks, artists, albums, and their popularity on Spotify.

## Dataset Information

- **Source**: [Provide the source or origin of the dataset]
- **Format**: [Specify the format of the dataset, e.g., CSV, SQL]
- **Fields**: [List the fields/columns present in the dataset]

## SQL Queries

The following SQL queries were used to prepare the dataset for analysis and visualization using Tableau.

### 1. Convert Milliseconds to Minutes

```sql
-- Convert milliseconds to minutes
UPDATE Originalsql
SET duration_ms = duration_ms / 60000;
```

### 2. Remove Unnecessary Columns

```sql
-- Drop Track ID Column and Unnamed Info not required for analysis
ALTER TABLE Originalsql
DROP COLUMN track_id;

ALTER TABLE Originalsql
DROP COLUMN Unnamed_0;
```

### 3. Group by Artists, Albums, Popularity, and Track Genre

```sql
-- Select specific columns and group by artists, album_name, popularity, and track_genre
SELECT artists, album_name, popularity, track_genre
FROM Originalsql
GROUP BY artists, album_name, popularity, track_genre;
```

### 4. Count Album Appearances

```sql
-- Count the number of appearances of each album
SELECT album_name, COUNT(album_name) as Album_appearance
FROM Originalsql 
GROUP BY album_name;
```

### 5. Group by Artists, Track Name, and Popularity

```sql
-- Select specific columns and group by artists, track_name, and popularity
SELECT artists, track_name, popularity
FROM Originalsql
GROUP BY artists, track_name, popularity;
```

### 6. Count Artist Appearances

```sql
-- Count the number of appearances of each artist
SELECT artists, COUNT(artists) as Artist_Appearance
FROM Originalsql
GROUP BY artists;
```

## Usage with Tableau

The preprocessed data can be easily imported into Tableau for further analysis and visualization. The transformed tables can be connected to Tableau for creating interactive and insightful dashboards.

## Conclusion

This documentation provides an insight into the Spotify dataset and the steps taken to preprocess the data for analysis. The SQL queries transform the raw data into smaller, more manageable tables suitable for visualization tools like Tableau.

