# Setup of development environment

## 1. Setup OS (Operating System)

### 1.1 Ubuntu
#### 1.1.1 Install
#### 1.1.2 Update

> sudo apt-get update

#### 1.1.3 Install packed software and libraries

> sudo apt-get install autoconf automake bison build-essential curl libc6-dev libreadline6 libreadline6-dev
libsqlite3-0 libsqlite3-dev libssl-dev libtool libxml2-dev libxslt-dev libxslt1-dev libyaml-dev ncurses-dev 
openssl sqlite3 zlib1g zlib1g-dev pkg-config

#### 1.1.4 Install git

> sudo apt-get install git

or

> sudo apt-get install git-core

### 1.2 VirtualBox
#### 1.2.1 Install or Update
download, install, start, create vm

#### 1.2.2 Configure
install Guest User Additions in started VM via TopLevelMenue

setup RAM, CPUs, Graphic Memory, HD before install of OS

restart if necessary

## 2. Setup RVM (Ruby Version Manager)

### 2.2 Install as single user

> curl -L get.rvm.io | bash -s stable

### 2.2 Configure

set terminal to run command as a login shell

### 2.2 Update

## 3. Setup Database
### 3.1 Postgresql
#### 3.1.1 Install

> sudo apt-get install postgresql libpq-dev

## 3. Setup project

### 3.1 Install Ruby

> rvm install 1.9.3

### 3.2 Create rvm gemset

switch to correct ruby in rvm session in terminal

> rvm use ruby-1.9.3-p194-perf@global

TODO: clearify why default gemset does not work

make sure correct ruby is loaded in rvm session in terminal

> ruby -v
> ruby 1.9.3p194 (2012-04-20 revision 35410) [x86_64-linux]

create gemset

> rvm gemset create app_name

make sure correct gemset is loaded in rvm session in terminal

> rvm gemset name

 check for recent needed gems for development with rails

> gem li
> *** LOCAL GEMS ***

add if needed (usually installed by default) TODO: clearify why not with perf-patch

> gem install bundler
> gem install rake
> gem install rubygems-bundler
> gem install rvm

for development with rails install rails now

for latest version

> gem install rails

### 3.3 Create project

cd into your workspace
create your rails app

> rails new app_name

### 3.4 Create .rvmrc

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
