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

## 2. Setup RVM (Ruby Version Manager)

### 2.2 Install as single user

> curl -L get.rvm.io | bash -s stable

### 2.2 Configure

set terminal to run command as a login shell

### 2.2 Update

## 3. Setup project

### 3.1 Install Ruby

> rvm install 1.9.3

### 3.2 Create rvm gemset

### 3.3 Create project

### 3.4 Create .rvmrc

### 3.5 Setup gems
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
