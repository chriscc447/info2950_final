# Final Project for INFO2950
Group members: Chris Chen, Michael Schwartz, Will Bekerman


## Info about files:

* __scraper_TopCharts.ipynb__: this is the scraper that was used to scrape data off of Spotify’s top charts webpages starting from 1/1/17 until 4/13/20 (ex: https://spotifycharts.com/regional/us/daily/2020-03-22). These pages only contain *basic information* about each song, such as the song’s rank on the given day, its number of streams, its title, and the artist. After running the scaper, the final dataset was stored in the __TopCharts_incomplete.csv__ file.
* __scraper_AudioFeatures.ipynb__: this is the scraper that was used to retrieve audio features (such as Tempo, Valence, Energy etc.) for each song in the __TopCharts_incomplete.csv__ using Spotify’s API. After I ran this scraper, some queries returned nothing, resulting in the dataset containing NA values. This data was stored in the __TopCharts_missing.csv__ file. I then fixed some of the errors, but others persisted (possibly because those songs no longer exist on Spotify).The resulting data is stored in the __TopCharts_complete.csv__ file.
  * Spotify's documentation on audio features: https://developer.spotify.com/documentation/web-api/reference/tracks/get-audio-features/ 
* __TopCharts_incomplete.csv__: scraped directly from Spotify's Top Charts website; does not contain audio features
* __TopCharts_missing.csv__: first round of retrieving audio features; some songs may be missing audio features
* __TopCharts_complete.csv__: complete dataset with all audio features
* __TopCharts.csv__: complete dataset with all audio features and streams converted to int datatype
* __TopCharts_clustered_artists.csv__: dataset with all unique artists, their median audio feature values, and their cluster assignments
* __TopCharts_clustered_songs.csv__: dataset with all unique songs and their cluster assignments

## Some issues regarding the dataset:
* Spotify doesn’t have Top Charts webpages for the following dates:
  * 2017-05-30
  * 2017-05-31
  * 2017-06-02
* Some Top Charts webpages have missing values for the artist and song name (ex: ranks 8, 16, 33, 63 on https://spotifycharts.com/regional/us/daily/2017-07-20). The rows with missing artist and songs names were ignored during scraping.
* Some songs on past Top Charts don’t show up when searched for using Spotify’s query feature. However, these songs comprise a very small portion of our entire dataset (<2%), so we decided to exclude them in our final dataset (these missing songs are listed at the bottom of the scraper_AudioFeatures.ipynb file)
* There are duplicates in the CSV files (one row for each day a song is on the top charts), which could make the dataset hard to work with
* For example, when we examine the top song for each week, if the same song is still at the top, this could potentially confound our model of the change over time of the top song

