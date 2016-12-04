### Why implement a new show update method?
As of version x, a new way of show updating has been implemented.
Previously update files have been used from thetvdb. We've made changes to this to make this less dependent of the thetvdb update files, as 1. we're aiming to implement new indexers like tvmaze and 2. we don't how long these files will stay available, as thetvdb has moved from their xml api to a new swagger based rest api.

The new update code, will make use of a table, that will keep track on the shows, on a per season basis. This way we can make sure new running seasons will stay checked and updated on short intervals. While long running (older) shows, will 'refresh' on longer intervals.

The new update code will move through the following steps:
* Get a list of shows from db, with seasons which should be updated.
* Loop through this list.
* Get the indexer from which this show is indexed
* Get the episodes for the season that should be updated
* If it the running season (the last), check if the show has had a update through the api, and update only last season
* If it is a previous (backlog) season, just refresh that season.
* Update the 'next_update' timestamp for these seasons

### Calculating the next updates
The running season, is the last season of a series. It should get a default next_update of now() + 3600 seconds (1 hour update)

### Calculating previous seasons. For these the airdate of the last episode is taken. The following formula wil be used.
The delta will be taken from the airdate compared to now.

The next update is calculated by dividing the delta of the last air date by 200.
**Maybe this divider should be adjusted. As a show for which a new episodes hasn't aired for a year, could wait longer then 43 hours, for it's next check up.**

| last air date | delta seconds | next update seconds | next update hours | 
|--------------|---------------|---------------------|-------------------|
| 7 days       | 604800        | 3024                | 0,84              |
| 1 month      | 2592000       | 12960               | 3,6               |
| 1 year       | 31536000      | 157680              | 43,8              |
| 20 years     | 630720000     | 3153600             | 876               |
| Devider:     | 200           |                     |                   |

### Using indexer who provide per season updates (TMDB)
TMDB provides an api which you can query on a showid, which returns a list of seasons that have been updated for the show. When already being updated on a season level, we don't need to calculate the next season update.
For shows added through an indexer which supports this, we've added the indexers method: 'get_last_updated_seasons()'.

It will not iterate over the indexers, but start with the show list. And will add the show on a season or show level to the corresponding lists.