### Requirement ###
* Git
* A clone of [Sickrage repo](https://github.com/SiCKRAGETV/SickRage.git)

********

### Index ###
* Merge develop into master
* Merge a PR via command line
* Merge a hotfix(master and develop)

********

### Merge develop into master ###
Increment the tag number each time.
```
$ git checkout master
$ git merge --no-ff develop
$ git tag -a v4.0.12
$ git push origin master
$ git push --tags origin master
```

### Merge a PR via command line ###
* The PR must be merged into `SiCKRAGETV:develop`
* The branch we want to commit is `fernandog:remote_tvcache_traceback`
```
$ git checkout -b fernandog-remote_tvcache_traceback develop
$ git pull https://github.com/fernandog/SickRage.git remote_tvcache_traceback
$ git checkout develop
$ git merge --no-ff fernandog-remote_tvcache_traceback
$ git push origin develop
$ git branch -d fernandog-remote_tvcache_traceback
```

### Merge a hotfix(master and develop) ###
* The PR must be merged into `SiCKRAGETV:master`
* The branch we want to commit is `fernandog:remote_tvcache_traceback`
```
$ git checkout -b fernandog-remote_tvcache_traceback develop
$ git pull https://github.com/fernandog/SickRage.git remote_tvcache_traceback
$ git checkout master
$ git merge --no-ff fernandog-remote_tvcache_traceback
$ git push origin master
$ git checkout develop
$ git merge --no-ff fernandog-remote_tvcache_traceback
$ git push origin develop
$ git branch -d fernandog-remote_tvcache_traceback
```