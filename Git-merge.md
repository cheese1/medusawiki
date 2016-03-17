### Requirement ###
* Git
* A clone of [Medusa repo](https://github.com/PyMedusa/SickRage.git)

********

### Index ###
* [Merge develop into master](https://github.com/PyMedusa/SickRage/wiki/Git-merge#merge-develop-into-master)
* [Merge a PR via command line](https://github.com/PyMedusa/SickRage/wiki/Git-merge#Merge-a-PR-via-command-line)
* [Merge a hotfix(master and develop)](https://github.com/PyMedusa/SickRage/wiki/Git-merge#merge-a-hotfixmaster-and-develop)

********

### Merge develop into master ###
Increment the tag number each time.
```
$ git checkout master
$ git merge --no-ff develop
$ git tag -a v0.0.0
$ git push origin master
$ git push --tags origin master
```

### Merge a PR via command line ###
* The PR must be based on `SickRage:develop`
* The branch we want to commit is `{YOUR_GITHUB_USER}:branchABC`
```
$ git checkout -b branchABC develop
$ git pull https://github.com/{YOUR_GITHUB_USER}/SickRage.git branchABC
$ git checkout develop
$ git merge --no-ff branchABC
$ git push origin develop
$ git branch -d branchABC
```

### Merge a hotfix(master and develop) ###
* The PR must be based on `Medusa:master`
* The branch we want to commit is `{YOUR_GITHUB_USER}:branchABC`
```
$ git checkout -b branchABC master
$ git pull https://github.com/{YOUR_GITHUB_USER}/SickRage.git branchABC
$ git checkout master
$ git merge --no-ff branchABC
$ git push origin master
$ git checkout develop
$ git merge --no-ff branchABC
$ git push origin develop
$ git branch -d branchABC
```