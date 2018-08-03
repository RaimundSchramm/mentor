### Linux Console Style Guide

#### Contents
* [Open files in a web browser](#open-files-in-a-web-browser)
* [Copy files via SSH in command line](#copy-files-via-ssh-in-command-line)
* [Copy command output into a file](#copy-command-output-into-a-file)
* [Count lines](#count-lines)
* [Add name of current Git branch to prompt](#add-name-of-current-git-branch-to-prompt)
* [Add current gemset to prompt](#add-current-gemset-to-prompt)
* [Add multiline output for prompt](#add-multiline-output-for-prompt)
* [Add alias command for starting a rails server for prompt](#add-command-for-prompt-for-starting-rails-server)

#### Open files in a web browser

Assuming a web browser is installed, e.g. Mozilla Firefox,
enter the following statement into your console and press
enter.

```
firefox path_to_your_file
```
see for example
(http://www.howtogeek.com/howto/15781/open-a-file-browser-from-your-current-command-promptterminal-directory/)

#### Copy files via SSH in command line

Assuming two computers in an accessable network and SSH setup,
enter the following statment into your console and press enter.

```
scp user@from-host:path-to-source-file path-to-destination-file
```
see for example
(http://www.garron.me/en/linux/scp-linux-mac-command-windows-copy-files-over-ssh.html)

#### Copy command output into a file

I want to see and work with the output of any terminal command inside my favourite text editor.

```
git show huge-commit &> path-to-your-output-file
```
[see example here](http://stackoverflow.com/questions/2840187/how-to-pipe-the-output-of-a-command-to-file-on-linux)

#### Count lines

I want to see how many commits I did since a certain date. So I can use `wc -l` (note: it is a small L and not a 1 :D ).

```
git log --oneline --since 2016-03-01 | wc -l
```

#### Add name of current Git branch to prompt

[for example](http://martinvalasek.com/blog/current-git-branch-name-in-command-prompt)

#### Add current gemset to prompt

[for example](http://stackoverflow.com/questions/3294072/bash-get-last-dirname-filename-in-a-file-path-argument)

#### Add multiline output for prompt

[for example](http://askubuntu.com/questions/251154/long-lines-overlap-in-bash-ps1-customized-prompt)
[and more](https://www.maketecheasier.com/8-useful-and-interesting-bash-prompts/)
[something about environment variables](https://www.digitalocean.com/community/tutorials/how-to-read-and-set-environmental-and-shell-variables-on-a-linux-vps)

#### Add command for prompt for starting rails server

I want to start a rails server with an alias. I want to skip changing directory and entering rails command.

To use for example the following alias
```
gemoriaprod
```
I need to open my ~/.bashrc inside my home directory and add a similar line.

alias name-of-alias-command='cd ~/path-to-app && rails s [options-of-choice]'
```
alias gemoriaprod='cd ~/projects/tools/gemoria && rails s -e production -p 3010'
```
