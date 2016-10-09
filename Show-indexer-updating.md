# Show indexer Updating

As of version x, a new way of show updating has been implemented.
Previously update files have been used from thetvdb. We've made changes to this to make this less dependent of the thetvdb update files, as 1. we're aiming to implement new indexers like tvmaze and 2. we don't how long these files will stay available, as thetvdb has moved from their xml api to a new swagger based rest api.

The new update code, will make use of a table, that will keep track on the shows, on a per season basis. This way we can make sure new running seasons will stay checked and updated on short intervals. While long running (older) shows, will 'refresh' on longer intervals.

The new update code will move through the following steps:
1. Get a list of shows from db, with seasons with should be updated.
2. Loop through this list.
2.a Get the indexer for wich this show is indexed
2.b Get the episodes for the season that should be updated
2.c If it the running season (the last), check if the show has had a update through the api, and update only last season
3.d If it is a previous (backlog) season, just refresh that season.
4 Update 'next_update' for these seasons

# Calculating the next updates
The running season, is the last season of a series. It should get a default next_update of now() + 3600 seconds (1 hour update)

# Calculating previous seasons. For these the airdate of the last episode is taken. The following formula wil be used.
The delta will be taken from the airdate compared to now.

The next update is calculated by deviding the delta of the last airdate by 200.
