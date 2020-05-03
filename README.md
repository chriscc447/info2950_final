# Final Project for INFO2950
Group members: Chris Chen, Michael Schwartz, Will Bekerman


## Info about files:

* __scraper_TopCharts.ipynb__: this is the scraper that was used to scrape data off of Spotify’s top charts webpages starting from 1/1/17 until 4/13/20 (ex: https://spotifycharts.com/regional/us/daily/2020-03-22). These pages only contain *basic information* about each song, such as the song’s rank on the given day, its number of streams, its title, and the artist. After I ran this scraper, the resulting data was stored in the __TopCharts_incomplete.csv__ file.
* __scraper_AudioFeatures.ipynb__: this is the scraper that was used to retrieve audio features (such as Tempo, Valence, Energy etc.) for each song in the __TopCharts_incomplete.csv__ using Spotify’s API. The resulting data is stored in the __TopCharts_complete.csv__ file.
  * Spotify's documentation on audio features: https://developer.spotify.com/documentation/web-api/reference/tracks/get-audio-features/ 
* __TopCharts_skeleton.csv__: scraped directly from Spotify's Top Charts website; does not contain audio features
* __TopCharts_incomplete.csv__: first round of retrieving audio features; some songs may be missing audio features
* __TopCharts_complete.csv__: complete dataset with all audio features

## Some issues regarding the dataset:
* Spotify doesn’t have Top Charts webpages for the following dates:
  * 2017-05-30
  * 2017-05-31
  * 2017-06-02
* Some songs on past Top Charts don’t show up when searched for using Spotify’s query feature. However, these songs comprise a very small portion of our entire dataset (<2%), so we decided to exclude them in our final dataset

