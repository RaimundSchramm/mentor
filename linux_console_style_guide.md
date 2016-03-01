###Linux Console Style Guide

####Contents
* [Open files in a web browser](#Open files in a web browser)
* [Copy files via SSH in command line](#Copy files via SSH in command line)
* [Copy command output into a file](#copy-command-output-into-a-file)

####Open files in a web browser

Assuming a web browser is installed, e.g. Mozilla Firefox,
enter the following statement into your console and press
enter.

```
firefox path_to_your_file
```
see for example
(http://www.howtogeek.com/howto/15781/open-a-file-browser-from-your-current-command-promptterminal-directory/)

####Copy files via SSH in command line

Assuming two computers in an accessable network and SSH setup,
enter the following statment into your console and press enter.

```
scp user@from-host:path-to-source-file path-to-destination-file
```
see for example
(http://www.garron.me/en/linux/scp-linux-mac-command-windows-copy-files-over-ssh.html)

####Copy command output into a file

I want to see and work with the output of any terminal command inside my favourite text editor.

```
git show huge-commit &> path-to-your-output-file
```
[see example here](http://stackoverflow.com/questions/2840187/how-to-pipe-the-output-of-a-command-to-file-on-linux)
