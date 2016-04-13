###Git Style Guide

#### Contents
1. [First Time Setup](#first-time-setup)
2. [Fork and Pull](#fork-and-pull)
3. [Useful History](#useful-history)
  - 1 Approach
  - 2 Contributing Something
  - 3 [Typical Workflow](#3-typical-workflow)
  - 4 [Alternative Workflow with implicit Testing](#4-alternative-workflow-with-implicit-testing)
  - 5 [Git Workflows](#5-git-workflows)
  - 6 [Release Management](#6-release-management)

-

#### First Time Setup

Install git `sudo apt-get install git`

Add your name and email to the global git configuration file

```
git config --global user.name 'Your Name'
git config --global user.email 'your@email.com'
```

Initialize new repository locally:

```
mkdir target-directory && cd target-directory
git init
git add .
git commit -m 'initializes repository'
git remote add origin remote-url
git push -u origin master
```

or create new repository for example on github and clone it:

```
git clone https://github.com/githubuser/repository.git [target-directory]
cd repository / [targetdirectory]
etc.
```


-

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

-

#### Useful History

With Git lots of information can reside inside a repository's history. If you take a careful and disciplined approach maintaining your commits and their messages you can use them to get any information.

##### 1 General approach

The idea is to get a complete and nicely formatted overview of important information used in day-to-day work. This could be for example to see a complete list of maintaining a certain gem.

Therefore you need a best practice approach paired with a certain style guide.

Try something like using certain keywords and a strict order to combine a commit message with lookup information.

The desired output could be something like:

```
* db05189 2016-02-28 | updates version: 4.2.5.2 of gem: Rails for purpose: security fix
* 59eff40 2016-02-28 | uses version: 4.2.5.1 of gem: Rails for purpose: desired target version ~> 4.2 [Raimund Schramm]
```
The first task is to think of git log scenarios and make up good names for key concepts and items.

-

##### 2 Contributing something

A contribution can either be something that enters the repository for the first time in history or changes something that already existed. Maybe we should distinguish on a per-file-base at first.

concept|keyword
---|---
a new file is added to the repository|**adds**
an existing file is modified|**updates**

The keyword for contributing something new is `adds`.

concept|keyword
---|---
a single test for a model|**Model Test**
a single test for a controller|**Controller Test**
a single test for a route|**Routing Test**
a single test for a Feature|**Integration Test**
a single test for a helper|**Helper Test**
a single test for a mailer|**Mailer Test**
a single test for a view|**View Test**

An elemental item which is contributed and follows the `adds` keyword could be a `Model Test`.

Examples for commit message:

```
adds Model Test for User model - favourite
adds Model Test for User
adds Model Test for User model
adds Model Spec for User - RSpec-related
```

-

##### 3 Typical Workflow

In BDD a typical Workflow could look like this (Rails-Full-Stack-Example):

1. Write a failing Integration Test - Some new feature is available in the View
  - Integration Test fails => Element Error
  -1.1 implement Element, for example a link => Integration Test passes
  -1.2 enhance Test, link requests an Action
  - Integration Test fails => Routing Error (ActionController::RoutingError: No route matches ...)
2. Write a failing Routing Test - Something new is in routes.rb
  - Routing Test fails => No route matches
  -2.1 implement Route => Routing Test fails => LoadError: Unable to autoload constant
3. Write a failing Controller Test - a new route is handled by a controller
  - Controller Test fails => Controller Error
  - 3.1 implement Controller => Action Error
4. Write a failing Controller Test for the Action
  - Controller Test fails => Action Error (not for new, see comments below)
  -4.1 implement Action inside Controller => View Error
  -4.2 implement View
5. Write a failing Integration Test for Data Model => Model Error
6. Write a failing Model Test => Model Error
  - 6.1 implement Model
7. Write a failing Controller Test using Model => Controller Error
  - 7.1 implement Model inside Controller Action => View Error
  - 7.2 implement Model inside View

=> Integration Test should be green

Comments:
- Controller Test for new action seems to not need implementation if route exists - why?
- add example

-

##### 4 Alternative Workflow with implicit Testing

Implement a Feature like:

1. Integration Test
  - implement View
  - implicit Routing Test ---> implement Route
  - implicit Controller Test ---> implement Controller and Actions
2. Model Test
  - implement Model and Methods

Comments:
- add example

-

##### 5 Git Workflows
When I started learning and using git I commited everything in the Master Branch.
Later I followed the recommendation to use Feature Branches for a better commit management. This is what I still do today.
My goal is to someday apply an even better approach like these resources suggest:

- [A successful Git branching model](http://nvie.com/posts/a-successful-git-branching-model/)
- [Several Workflows](https://www.atlassian.com/git/tutorials/comparing-workflows/)

-

##### 6 Release Management

use semantic versioning

- https://help.github.com/articles/closing-issues-via-commit-messages/

-
