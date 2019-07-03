# Kinda needs an API documentation page... Rough start

- *API* &mdash; the API URL, default is `http://localhost:8081/api/v2`

> API/config &mdash; get the user's configuration

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
		"selectedRootIndex": -1,
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