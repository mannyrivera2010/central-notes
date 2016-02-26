### Todolist Using Version Control REST Ideas
## Features
 - Ability to have many todolists (millions)
 - High Requests/Seconds at Peak Requests
 - Offine Mode
 - Concurrent Changes

## Client - Server
 - To the client every todolist is a version controlled object
 - All playlists of a user is synced on login
 -- Fetch all new changes

## Reference
http://www.slideshare.net/planetcassandra/c-summit-eu-2013-playlists-at-spotify-using-cassandra-to-store-version-controlled-objects

### Planning a Data Model
 - Three Common Playlist Operations
  - SYNC: Get all changes since a particular revision
  - GET: Get the most recent snapshot
  - APPEND: Add/Move/Delete Tracks

### Data Model Using 


Inspired by http://www.slideshare.net/planetcassandra/c-summit-eu-2013-playlists-at-spotify-using-cassandra-to-store-version-controlled-objects