###Git Style Guide

####Fork and Pull

assuming
- github account is set up (Contributor)
- there is an issue in some target repo (Maintainer)
- target repo is forked (forked from Maintainer's page)
- development environment is set up (for git and anything else needed)
- forked repo (remote origin master of Contributor) is cloned
- working directory is clean and repo up-to-date

#####1. Check out a feature branch.

```
git commit -b branch-to-solve-issue
```

#####2. Solve the issue and commit.

```
git add .
git commit -m 'solves issue'
```

#####3. Push local feature branch to remote origin (forked repo)

```
git push origin branch-to-solve-issue
```

#####4. Creating and sending Pull Request
As Contributor:
- Go to forked repo page on github
- switch to feature branch
- click 'Compare and Review'
- click 'Send pull request'

#####5. Mergin Pull Request
As Maintainer:
- Go to repo on github and find pull request
- Merge automatically via github or
- Merge manually on command line:

a) checkout local branch to merge
```
git checkout contributor-branch-to-solve-issue master
```
b) pull branch from Contributor
```
git pull https://github.com/Contributor/forked-repository.git branch-to-solve-issue
```
c) resolve any conflicts and review/check (i.e. run tests)
d) merge into destination branch
```
git checkout master
git merge --no-ff contributor-branch-to-solve-issue
```
e) push to origin
```
git push origin master
```
#####6. Clean up feature branch
As contributor:
- click on '...' on your github page
- in your local repo pull up-to-date version from upstream (Maintainer)
```
git pull upstream master
```
- delete obsolete branch locally
```
git branch -d branch-to-solve-issue
```
As maintainer:
- delete obsolete branch locally, see above.
