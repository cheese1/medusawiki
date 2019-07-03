# Kinda needs an API documentation page... Rough start

> *API* &mdash; the API URL, default is `http://localhost:8081/api/v2`

----

<details>
<summary> <b>API</b>/config &mdash; get the user's configuration </summary>
<article>

```javascript
{
	"clients": {
		"torrents": {
			"authType": <String>,		// the authorization type (if applicable)
			"dir": <String:folder>,		// the DIR to the torrent's executable*?
			"enabled": <Boolean>,		// self explanatory
			"highBandwidth": <Boolean>,	// self explanatory
			"host": <String:URL>,		// the URL to the user's torrent searcher
			"label": <String>,		// the label to add (if applicable)
			"labelAnime": <String>,		// label for anime
			"method": <String>,		// the torrent searcher to use
			"path": <String:folder>,	// DIR to the searcher's download path
			"paused": <Boolean>,		// add in the paused state?
			"rpcUrl": <String>,		// the torrent search type ("transmission", etc.)
			"seedLocation": <String>,	// the seeding location
			"seedTime": <Number>,		// the time allowed to seed (upload)
			"username": <String>,		// self explanatory
			"password": <String>,		// self explanatory
			"verifySSL": <Boolean>		// check for proper SSL?
		},
		"nzb": {
			"enabled": <Boolean>,
			"dir": <String:folder>,
			"method": <String>,
			"nzbget": <Object>,
			"sabnzbd": <Object>
		}
	},
	"consts": {
		"qualities": {
			"values": <Array:Object>,
			"anySets": <Array:Object>,
			"presets": <Array:Object>
		},
		"statuses": <Array:Object>
	},
	"main": {
		"anonRedirect": <String>,
		"animeSplitHome": <Boolean>,
		"animeSplitHomeInTabs": <Boolean>,
		"comingEpsSort": <String>,
		"comingEpsDisplayPaused": <Boolean>,
		"datePreset": <String>,
		"fuzzyDating": <Boolean>,
		"themeName": <String:Enum[dark*, light]>,
		"posterSortby": <String>,
		"posterSortdir": <Number>,
		"rootDirs": <Array:String>,
		"sortArticle": <Boolean>,
		"timePreset": <String>,
		"trimZero": <Boolean>,
		"fanartBackground": <Boolean>,
		"fanartBackgroundOpacity": <Number:Float>,
		"gitUsername": <String>,
		"branch": <String:Enum[master*, develop]>,
		"commitHash": <String>,
		"release": <String>,
		"sslVersion": <String>,
		"pythonVersion": <String>,
		"databaseVersion": {
			"major": <Number>,
			"minor": <Number>
		},
		"os": <String>,
		"pid": <Number>,
		"locale": <String>,
		"localUser": <String>,
		"programDir": <String:folder>,
		"dataDir": <String:folder>,
		"configFile": <String:file>,
		"dbPath": <String:file>,
		"cacheDir": <String:folder>,
		"logDir": <String:folder>,
		"appArgs": <Array:String>,
		"webRoot": <String>,
		"runsInDocker": <Boolean>,
		"githubUrl": <String:URL>,
		"wikiUrl": <String:URL>,
		"donationsUrl": <String:URL>,
		"sourceUrl": <String:URL>,
		"downloadUrl": <String:URL>,
		"subtitlesMulti": <Boolean>,
		"namingForceFolders": <Boolean>,
		"subtitles": {
			"enabled": <Boolean>
		},
		"recentShows": <Array:Object>,
		"randomShowSlug": <String>,
		"showDefaults": {
			"status": <Number>,
			"statusAfter": <Number>,
			"quality": <Number>,
			"subtitles": <Boolean>,
			"seasonFolders": <boolean>,
			"anime": <Boolean>,
			"scene": <Boolean>
		},
		"news": {
			"lastRead": <String:Date[YYYY-MM-DD]>,
			"latest": <String:Date[YYYY-MM-DD]>,
			"unread": <Number>
		},
		"logs": {
			"debug": <Boolean>,
			"dbDebug": <Boolean>,
			"loggingLevels": {
				"error": <Number>,
				"warning": <Number>,
				"info": <Number>,
				"debug": <Number>,
				"db": <Number>
			},
			"numErrors": <Number>,
			"numWarnings": <Number>
		},
		"failedDownloads": {
			"enabled": <Boolean>,
			"deleteFailed": <Boolean>
		},
		"layout": {
			"schedule": <String>,
			"history": <String>,
			"home": <String>,
			"show": {
				"allSeasons": <Boolean>,
				"specials": <Boolean>,
				"showListOrder": <Array>
			}
		},
		"selectedRootIndex": <Number>,
		"backlogOverview": {
			"period": <String>,
			"status": <String>
		},
		"indexers": {
			"config": {
				"indexers": <Object>,
				"main": {
					"validLanguages": <Array:ISO-Languages>,
					"langabbvToId": <Object:ISO-Languages>,
					"externalMappings": <Object>,
					"traktIndexers": {
						"tvdb": <Number>,
						"tmdb": <Number>,
						"imdb": <Number>,
						"trakt": <Number>
					},
					"statusMap": {
						"returning series": <String:Enum[Continuing*, Ended]>,
						"canceled/ended": <String:Enum[Continuing, Ended*]>,
						"tbd/on the bubble": <String:Enum[Continuing*, Ended]>,
						"in development": <String:Enum[Continuing*, Ended]>,
						"new series": <String:Enum[Continuing*, Ended]>,
						"never aired": <String:Enum[Continuing, Ended*]>,
						"final season": <String:Enum[Continuing*, Ended]>,
						"on hiatus": <String:Enum[Continuing*, Ended]>,
						"pilot ordered": <String:Enum[Continuing*, Ended]>,
						"pilot rejected": <String:Enum[Continuing, Ended*]>,
						"canceled": <String:Enum[Continuing, Ended*]>,
						"ended": <String:Enum[Continuing, Ended*]>,
						"to be determined": <String:Enum[Continuing*, Ended]>,
						"running": <String:Enum[Continuing*, Ended]>,
						"planned": <String:Enum[Continuing*, Ended]>,
						"in production": <String:Enum[Continuing*, Ended]>,
						"pilot": <String:Enum[Continuing*, Ended]>,
						"cancelled": <String:Enum[Continuing, Ended*]>,
						"continuing": <String:Enum[Continuing*, Ended]>
					}
				}
			}
		},
		"postProcessing": {
			"naming": {
				"pattern": <String:Pattern>,
				"multiEp": <Number>,
				"patternAirByDate": <String:Pattern>,
				"patternSports": <String:Pattern>,
				"patternAnime": <String:Pattern>,
				"enableCustomNamingAirByDate": <Boolean>,
				"enableCustomNamingSports": <Boolean>,
				"enableCustomNamingAnime": <Boolean>,
				"animeMultiEp": <Number>,
				"animeNamingType": <Number>,
				"stripYear": <Boolean>
			},
			"showDownloadDir": <String:folder>,
			"processAutomatically": <Boolean>,
			"postponeIfSyncFiles": <Boolean>,
			"postponeIfNoSubs": <Boolean>,
			"renameEpisodes": <Boolean>,
			"createMissingShowDirs": <Boolean>,
			"addShowsWithoutDir": <Boolean>,
			"moveAssociatedFiles": <Boolean>,
			"nfoRename": <Boolean>,
			"airdateEpisodes": <Boolean>,
			"unpack": <Boolean>,
			"deleteRarContent": <Boolean>,
			"noDelete": <Boolean>,
			"processMethod": <String>,
			"reflinkAvailable": <Boolean>,
			"autoPostprocessorFrequency": <Number>,
			"syncFiles": <Array>,
			"fileTimestampTimezone": <String>,
			"allowedExtensions": <Array>,
			"extraScripts": <Array>,
			"extraScriptsUrl": <String:URL>,
			"multiEpStrings": {
				"1": <String>,
				"2": <String>,
				"4": <String>,
				"8": <String>,
				"16": <String>,
				"32": <String>
			}
		}
	},
	"metadata": {
		"metadataProviders": <Object>
	},
	"notifiers": <Object>,
	"search": {
		"general": {
			"randomizeProviders": <Boolean>,
			"downloadPropers": <Boolean>,
			"checkPropersInterval": <String>,
			"propersSearchDays": <Number>,
			"backlogDays": <Number>,
			"backlogFrequency": <Number>,
			"minBacklogFrequency": <Number>,
			"dailySearchFrequency": <Number>,
			"minDailySearchFrequency": <Number>,
			"removeFromClient": <Boolean>,
			"torrentCheckerFrequency": <Number>,
			"minTorrentCheckerFrequency": <Number>,
			"usenetRetention": <Number>,
			"trackersList": <Array:URL>,
			"allowHighPriority": <Boolean>,
			"useFailedDownloads": <Boolean>,
			"deleteFailed": <Boolean>,
			"cacheTrimming": <Boolean>,
			"maxCacheAge": <Number>
		},
		"filters": {
			"ignored": <Array>,
			"undesired": <Array>,
			"preferred": <Array>,
			"required": <Array>,
			"ignoredSubsList": <Array>,
			"ignoreUnknownSubs": <Boolean>
		}
	},
	"system": {
		"memoryUsage": <String>,
		"schedulers": [
			{
				"key": <String>,
				"name": <String>,
				"isAlive": <Boolean>,
				"isEnabled": <Boolean>,
				"isActive": <Boolean>,
				"startTime": <Date>,
				"cycleTime": <Number>,
				"nextRun": <Number>,
				"lastRun": <String>,
				"isSilent": <Boolean>
			}, // ...
		],
		"showQueue": <Array>
	}
}
```

</article>
</details>

----

<details>
<summary> <b>API</b>/internal/searchIndexersForShowName?query=<code>{showName}</code>&indexerId=<code>Number</code>&language=<code>ISO-Language</code> </summary>
<article>

```javascript
{
	"results": [
		[
			<String>,					// The provider's name, e.g. "TVMaze," "TMDB," etc.
			<Number>,					// The index of the provider (via the user's settings)*?
			<String:URL>,				// The provider's URL (homepage)
			<Number>,					// The show's ID
			<String>,					// The show's name
			<String:Date[YYYY-MM-DD]>,	// The show's premiere date
			<String>,					// The show's production network, e.g. Amazon Prime
			<String>,					// The show's local name
			[
				<String>,				// The provider's short name, e.g. "tmdb"
				<Number>				// The show's ID for the provider
			]
		], // ...
	],
	"languageId": <Number>
}
```

</article>
</details>

- *showName* &mdash; replace all spaces with `+`, e.g. `tv show` &rightarrow; `tv+show`

----

<details>
<summary> <b>API</b>/series/<code>{idProvider}{showID}</code>?detailed=<code>Boolean</code> </summary>
<article>

```javascript
{
	"id": {
		"tvdb": <Number>,
		"imdb": <String>,
		"slug": <String>,
		"trakt": <Object>
	},
	"title": <String>,
	"indexer": <String>,
	"network": <String>,
	"type": <String>,
	"status": <String>,
	"airs": <String:Date/Time>,
	"airsFormatValid": <Boolean>,
	"language": <String:ISO-Language>,
	"showType": <String:Enum>,
	"imdbInfo": {
		"countries": <String>,
		"countryCodes": <String>,
		"imdbId": <String>,
		"title": <String>,
		"year": <String>,
		"akas": <String>,
		"genres": <String>,
		"rating": <String>,
		"votes": <String>,
		"runtimes": <String:Time>,
		"certificates": <String>,
		"plot": <String>,
		"lastUpdate": <String:Date>
	},
	"year": {
		"start": <String>,
		"stop": <String>
	},
	"nextAirDate": <Object>,
	"runtime": <String:Time>,
	"genres": <Array:String>,
	"rating": {
		"imdb": {
			"rating": <String>
			"votes": <Number>
		}
	},
	"classification": <String>,
	"cache": {
		"poster": <String:file>,
		"banner": <String:file>
	},
	"countries": <Array:String>,
	"countryCodes": <Array:String>,
	"plot": <String>,
	"config": {
		"location": <String:folder>,
		"locationValid": <Boolean>,
		"qualities": {
			"allowed": <Array:Number>,
			"preferred": <Array>
		},
		"paused": <Boolean>,
		"airByDate": <Boolean>,
		"subtitlesEnabled": <Boolean>,
		"dvdOrder": <Boolean>,
		"seasonFolders": <Boolean>,
		"anime": <Boolean>,
		"scene": <Boolean>,
		"sports": <Boolean>,
		"defaultEpisodeStatus": <String:Enum>,
		"aliases": <Array>,
		"release": {
			"ignoredWords": <array:String>,
			"requiredWords": <array:String>,
			"ignoredWordsExclude": <Boolean>,
			"requiredWordsExclude": <Boolean>,
			"blacklist": <array:String>,
			"whitelist": <array:String>
		},
		"airdateOffset": <Number>
	},
	"size": <Number:Size>,
	"seasons": [
		[
			{
				"identifier": <String>,
				"id": <Object>,
				"season": <Number>,
				"episode": <Number>,
				"airDate": <String:Date/Time>,
				"title": <String>,
				"description": <String>,
				"content": <Array>,
				"subtitles": <Array>,
				"status": <String>,
				"watched": <Boolean>,
				"quality": <Number>,
				"release": {
					"name": <String>,
					"group": <String>,
					"proper": <Boolean>,
					"version": <Number>
				},
				"scene": {
					"season": <Number>,
					"episode": <Number>
				},
				"file": {
					"location": <String:folder>
				},
				"statistics": {
					"subtitleSearch": {
						"last": <String:Date>,
						"count": <Number>
					}
				},
				"wantedQualities": <Array>
			}
		], // ...
	],
	"episodeCount": <Number>,
	"showQueueStatus": [
		{
			"action": <String:"isBeingAdded">,
			"active": false,
			"message": "This show is in the process of being downloaded - the info below is incomplete"
		},
		{
			"action": <String:"isBeingUpdated">,
			"active": <Boolean>,
			"message": <String>
		},
		{
			"action": <String:"isBeingRefreshed">,
			"active": <Boolean>,
			"message": <String>
		},
		{
			"action": <String:"isBeingSubtitled">,
			"active": <Boolean>,
			"message": <String>
		},
		{
			"action": <String:"isInRefreshQueue">,
			"active": <Boolean>,
			"message": <String>
		},
		{
			"action": <String:"isInUpdateQueue">,
			"active": <Boolean>,
			"message": <String>
		},
		{
			"action": <String:"isInSubtitleQueue">,
			"active": <Boolean>,
			"message": <String>
		}
	],
	"xemNumbering": <Array>
}
```

</article>
</details>

----

<details>
<summary> <b>API</b>/series?limit=<code>Number</code>&page=<code>Number</code> </summary>
<article>

```javascript
[
	{
		"id": {
			"tvdb": <Number>,
			"imdb": <String>,
			"slug": <String>,
			"trakt": <Object>
		},
		"title": <String>,
		"indexer": <String>,
		"network": <String>,
		"type": <String>,
		"status": <String>,
		"airs": <String:Date/Time>,
		"airsFormatValid": <Boolean>,
		"language": <String:ISO-Language>,
		"showType": <String:Enum>,
		"imdbInfo": {
			"countries": <String>,
			"countryCodes": <String>,
			"imdbId": <String>,
			"title": <String>,
			"year": <String>,
			"akas": <String>,
			"genres": <String>,
			"rating": <String>,
			"votes": <String>,
			"runtimes": <String:Time>,
			"certificates": <String>,
			"plot": <String>,
			"lastUpdate": <String:Date>
		},
		"year": {
			"start": <String>,
			"stop": <String>
		},
		"nextAirDate": <Object>,
		"runtime": <String:Time>,
		"genres": <Array:String>,
		"rating": {
			"imdb": {
				"rating": <String>
				"votes": <Number>
			}
		},
		"classification": <String>,
		"cache": {
			"poster": <String:file>,
			"banner": <String:file>
		},
		"countries": <Array:String>,
		"countryCodes": <Array:String>,
		"plot": <String>,
		"config": {
			"location": <String:folder>,
			"locationValid": <Boolean>,
			"qualities": {
				"allowed": <Array:Number>,
				"preferred": <Array>
			},
			"paused": <Boolean>,
			"airByDate": <Boolean>,
			"subtitlesEnabled": <Boolean>,
			"dvdOrder": <Boolean>,
			"seasonFolders": <Boolean>,
			"anime": <Boolean>,
			"scene": <Boolean>,
			"sports": <Boolean>,
			"defaultEpisodeStatus": <String:Enum>,
			"aliases": <Array>,
			"release": {
				"ignoredWords": <array:String>,
				"requiredWords": <array:String>,
				"ignoredWordsExclude": <Boolean>,
				"requiredWordsExclude": <Boolean>,
				"blacklist": <array:String>,
				"whitelist": <array:String>
			},
			"airdateOffset": <Number>
		}
	}, // ...
]
```

</article>
</details>
