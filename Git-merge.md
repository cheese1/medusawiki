### Requirement ###
* Git
* A clone of [Sickrage repo](https://github.com/SiCKRAGETV/SickRage.git)

********

### Index ###
* [Merge develop into master](https://github.com/SiCKRAGETV/SickRage/wiki/Git-merge#merge-develop-into-master)
* [Merge a PR via command line](https://github.com/SiCKRAGETV/SickRage/wiki/Git-merge#Merge-a-PR-via-command-line)
* [Merge a hotfix(master and develop)](https://github.com/SiCKRAGETV/SickRage/wiki/Git-merge#merge-a-hotfixmaster-and-develop)

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
* The PR must be based on `SiCKRAGETV:develop`
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
* The PR must be based on `SiCKRAGETV:master`
* The branch we want to commit is `fernandog:remote_tvcache_traceback`
```
$ git checkout -b fernandog-remote_tvcache_traceback master
$ git pull https://github.com/fernandog/SickRage.git remote_tvcache_traceback
$ git checkout master
$ git merge --no-ff fernandog-remote_tvcache_traceback
$ git push origin master
$ git checkout develop
$ git merge --no-ff fernandog-remote_tvcache_traceback
$ git push origin develop
$ git branch -d fernandog-remote_tvcache_traceback
```