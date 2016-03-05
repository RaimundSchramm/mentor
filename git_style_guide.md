###Git Style Guide

#### Contents
1. [Fork and Pull](#fork-and-pull)
2. [Useful History](#useful-history)

#### Fork and Pull

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

#### Useful History
With Git lots of information can reside inside its history. If you take a careful and disciplined approach maintaining your commits and their messages you can use them to get any information.

The idea is to get a complete and nicely formatted overview of important information used in day-to-day work. This could be for example to see a complete list of maintaining a certain gem.

Therefore you need a best practice approach paired with a certain style guide.

Try something like using certain keywords and a strict order to combine a commit message with lookup information.

The desired output could be something like:

```
* db05189 2016-02-28 | updates version: 4.2.5.2 of gem: Rails for purpose: security fix
* 59eff40 2016-02-28 | uses version: 4.2.5.1 of gem: Rails for purpose: desired target version ~> 4.2 [Raimund Schramm]
```
Make up good names for key concepts and items:

| keyword for contributing something - `adds`
| elemental item which is contributed and follows `adds` - `Model Test`
|
