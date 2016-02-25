## Setup of development environment

This guide helps you setting up an environment for development.

It covers everything important concerning the goal to develop with Ruby- or Rails-Projects on Ubuntu either inside Virtualbox or normal installation.

Contents:

1. [Set up OS (Operating System)](#1-set-up-os-operating-system)
  1. [Ubuntu](#11-ubuntu)

- 1.1.1 Installation
- 1.1.2 Update
- 1.1.3 Install packed software and libraries
- 1.1.4 Install version control
- 1.1.5 Install a Javascript Runtime Environment
- 2. Setup RVM (Ruby Version Manager)
- 2.2 Installation
- 2.3 Configure
- 2.4 Configure Rubygems
- 2.5 Update

### 1. Set up OS (Operating System)
In this first section everything you need on your OS is explained.

#### 1.1 Ubuntu

The instructions below are related to Ubuntu 12.04.

##### 1.1.1 Installation

Get and install the desired target OS as you wish. Using VirtualBox you can [download an iso-file](http://www.ubuntu.com/download) for example.

##### 1.1.2 Update

If there are any system updates available, for example after a fresh installation, first synchronize the package index file with its sources. Open a terminal and run `sudo apt-get update`.

Second, install the most recent version of each installed package. In your terminal run now `sudo apt-get upgrade`.

Third, you can uninstall obsolete dependencies of packages that were installed automatically. Run `sudo apt-get autoremove` inside the terminal if you wish.

##### 1.1.3 Install packed software and libraries

As I use RVM for Management of rubies and gems and it now takes care of initial requirements no additional libraries are required at this point.

Outdated:
> sudo apt-get install autoconf automake bison build-essential curl libc6-dev libreadline6 libreadline6-dev
libsqlite3-0 libsqlite3-dev libssl-dev libtool libxml2-dev libxslt-dev libxslt1-dev libyaml-dev ncurses-dev 
openssl sqlite3 zlib1g zlib1g-dev pkg-config

##### 1.1.4 Install version control

The choice is to use git as distributed version control system.
To install it run `sudo apt-get install git` or `sudo apt-get install git-core` in your terminal.

##### 1.1.5 Install a Javascrip Runtime Environment

The choice is to use node.js. Open your terminal and run `sudo apt-get install nodejs`.

#### 1.2 VirtualBox

##### 1.2.1 Install or Update

[download](https://www.virtualbox.org/wiki/Downloads), install, start, create vm

##### 1.2.2 Configure

Install Guest User Additions in started VM via TopLevelMenue.
Set up RAM, CPUs, Graphic Memory, HD before install of OS or after.
Restart virtual machine if necessary.

### 2. Setup RVM (Ruby Version Manager)

All Ruby-versions will be managed with RVM.

Note: To avoid any conflict it is better that no additional Ruby is installed outside RVM. If RVM is set up and used correctly than that should be no problem.

#### 2.2 Installation

Install RVM like explained on the [official page](https://rvm.io/rvm/install). In this guide installation as single user is chosen.

#### 2.3 Configure

Set terminal to run command as a login shell. Terminal Menue Bar -> Edit -> Profile Preferences -> Title and Command -> Run as Login Shell.

#### 2.4 Configure Rubygems

Create a .gemrc file inside your home directory and fill it with the desired [options](http://guides.rubygems.org/command-reference/), for example:
```
gem: --no-document
:backtrace: true
:sources:
- https://rubygems.org
```
For further .rc files see [this blogpost](http://www.justinweiss.com/articles/fast-consistent-setup-for-your-ruby-and-rails-projects/)

#### 2.5 Update

## 3. Setup Database
### 3.1 Postgresql
#### 3.1.1 Install

> sudo apt-get install postgresql

> sudo apt-get install libpq-dev

#### 3.1.2 set up postgres server

connect to postgres
> sudo -u postgres psql postgres

set password
> \password postgres

#### 3.1.3 create dbs via postgres in terminal

exit and create dbs
> sudo -u postgres createdb db-name-as-in-database.yml

#### 3.1.4 configure application

configure database.yml

```
development:
  adapter: postgresql
  encoding: unicode
  host: localhost
  username: {your-username}
  password: {your-password}
  database: {your-db-dev-name}
  pool: 5
```

### 3. Setup project

#### 3.1 Install Ruby

Install the desired version with RVM. Open a terminal and run `rvm install 2.1.5`.

There are [performance patches](https://github.com/skaes/rvm-patchsets) for the work with Ruby on Rails.

To install a performance patch run for example `rvm install 2.1.5 --patch railsexpress -n railsexpress`.

#### 3.2 Create RVM gemset

a) If it is a new project or there are no rvm-config-files (.ruby-version, .ruby-gemset) available

Switch to correct ruby in rvm session in terminal `rvm use ruby-2.1.5-railsexpress`.
Optional: Make sure correct ruby is loaded in rvm session in terminal `ruby -v`.

Create gemset `rvm gemset create name-of-gemset`
Optional: Make sure correct gemset is loaded in rvm session in terminal `rvm gemset name`.

Optional: Check for recent needed gems for development with rails. `gem li`.

Bundler seems to be removed as global gem (WHY?). It now seems that it has to be added to each gemset (-.-) with `gem install bundler`.

For development with rails install rails now `gem install rails`.

b) If it is an existing project and there are rvm-config-files (.ruby-version, .ruby-gemset) available

CD into the project directory - correct Ruby should be loaded by RVM and gemset should be created.

#### 3.3 Create project

cd into your workspace
create your rails app

> rails new app_name

#### 3.4 Create .rvmrc

cd into your app diretory
create .rvmrc for your project

> echo 'rvm use ruby-1.9.3-p194-perf@gemset_name' > .rvmrc

### 3.5 Setup git repository

cd into app directory

> git init
> git add .
> git commit -m "adds initial commit"

setup remote repository on github

configure local repository to work with remote

if ssh is setup

> git remote add origin git@github.com:YourGithubUserName/your_app_name.git

if local repo was set up first

> git pull origin master
> git push origin master

TODO: clearify why git pull is necessary
### 3.6 Setup gems

## 4. Setup IDE/Editor
### 4.1 Aptana Studio

visit http://www.aptana.com/

### 4.1.1 Install Oracle Java

according to prerequisites

http://www.aptana.com/products/studio3/getting_started

see

http://wiki.ubuntuusers.de/Java/Installation/Oracle_Java?redirect=no

and

http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html

> sudo add-apt-repository ppa:webupd8team/java

> sudo apt-get update

> sudo apt-get install oracle-java7-installer

### 4.2 Sublime Text 2

[set up sublime for console](https://github.com/mhartl/rails_tutorial_sublime_text)
