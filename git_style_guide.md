###Git Style Guide

####Fork and Pull

assuming
- github account is set up
- there is an issue in some target repo
- target repo is forked
- development environment is set up
- forked repo (remote origin master) is cloned
- working directory is clean and repo up-to-date

1. Check out a feature branch.

> git co -b branch-to-solve-issue

2. Solve the issue and commit.

```
  git add .
  git commit -m 'solves issue'
```

3. Push local feature branch to remote origin (forked repo)

> git push origin branch-to-solve-issue

4. As Contributor:
- Go to forked repo page on github
- switch to feature branch
- click 'Compare and Review'
- click 'Send pull request'

5. As Maintainer:
- Go to repo on github and find pull request
- Merge automatically via github or
- Merge manually on command line:
-- checkout local branch to merge
> git checkout contributor-branch-to-solve-issue master
-- pull branch from Contributor
> git pull https://github.com/Contributor/forked-repository.git branch-to-solve-issue
-- resolve any conflicts and review/check (i.e. run tests)
-- merge into destination branch
```
git co master
git git merge --no-ff contributor-branch-to-solve-issue
```
-- push to origin
> git push origin master

6. Clean up feature branch

