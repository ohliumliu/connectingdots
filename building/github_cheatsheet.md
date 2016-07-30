### Initial setup
1. Set up a repo in github.
1. On local machine, run`git init`, `git add -A` and then commit.
1. git remote add origin https://URL
1. git push -u origin master 

### Work with other remote
For gsl-playground, there are multiple remote as evidenced in `.git/config`. The first one was set up when I forked the repo from savannah. It can be added manually as well.
* Official repo:
```git
[remote "origin_official"]
        url = git://git.savannah.gnu.org/gsl.git
        fetch = +refs/heads/*:refs/remotes/origin_official/*
```
* My own fork:
```git
[remote "origin"]
        url = https://github.com/ohliumliu/gsl-playground.git
        fetch = +refs/heads/*:refs/remotes/origin/*
```
In principle, one could also set up different push and pull target for the same repo.
* Typical workflow:
  * on master branch, `git pull origin_official master` will get updated version from `origin_official`
  * on topic branch, `git rebase master` will move the topic branch on top of master branch. One could merge the topic branch to master if desired.
