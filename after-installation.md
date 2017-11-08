# Things to do after installation of Ubuntu
I have installed Ubuntu twice now and documented what I did. This document changes every time as I 
learn new things each time. To install Ubuntu, you need to go to the download site and also create a bootable usb key
you will use for the installation. That's easy. This downment shows you what to do afterwards.

## Install xclip
This program will let you copy your public key to the buffer.  It is needed when you upload your git key to gihub. 
It is also lets you paste into the terminal using <shift> <insert>

    sudo apt-get install xclip

## Install git
    sudo apt-get install git

## Set up the Github key.  See git hub instructions
https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/

## Install emacs
    sudo apt-get install emacs
   
## install el-get to emacs
https://github.com/dimitri/el-get
This will be the way Lisp packages are installed.

First you can use lisp to clone the el-get github repository.
```Lisp
;; So the idea is that you copy/paste this code into your *scratch* buffer,
;; hit C-j, and you have a working el-get.
(url-retrieve
 "https://raw.githubusercontent.com/dimitri/el-get/master/el-get-install.el"
 (lambda (s)
   (goto-char (point-max))
   (eval-print-last-sexp)))
```
Using the Basic Setup, copy this into the .emacs file
```{Lisp}
(add-to-list 'load-path "~/.emacs.d/el-get/el-get")

(unless (require 'el-get nil 'noerror)
  (with-current-buffe
      (url-retrieve-synchronously
       "https://raw.githubusercontent.com/dimitri/el-get/master/el-get-install.el")
    (goto-char (point-max))
    (eval-print-last-sexp)))

(add-to-list 'el-get-recipe-path "~/.emacs.d/el-get-user/recipes")
(el-get 'sync)
```

## markdown-mode to emacs
This lets you edit markdown code for pushing to github
I did not use el-get for this but should have.
https://stable.melpa.org/#/markdown-mode# 
``` Lisp
(require 'package)
(add-to-list 'package-archives
             '("melpa-stable" . "https://stable.melpa.org/packages/"))
(package-initialize)
```

## Install Mercurial
This will let you get the vim-mode el from bitbucket.
https://confluence.atlassian.com/get-started-with-bitbucket/mercurial-setup-860009660.html
sudo apt-get install mercurial

### clone vim-mode
hg clone https://bitbucket.org/lyro/vim-mode
https://www.emacswiki.org/emacs/VimMode

This might be doable with get-el.
Add to your .emacs file
```lisp
(add-to-list 'load-path "/path/to/vim-mode")
    (require 'v)
    (vim-mode 1)
```	
initiate viper mode in emacs

## Install markdown
https://www.emacswiki.org/emacs/MarkdownPreviewMode
This is needed so that ```markdown-preview mode works in in emacs
Actually livedown works better.

```bash
sudo apt-get install markdown
```

## Install preview mode
```emacs
   package-install markdown-preview-mode
```

## install livedown.
his is whay nodejs and npm was installed earlier.
https://github.com/shime/livedown



## Fix the wireless router
There seems to be a problem with my belkin usb wireless adapter.  
https://askubuntu.com/questions/902992/ubuntu-gnome-17-04-wi-fi-not-working-mac-address-keeps-changing
	
The  mac address is changes constantly as a security feature.
The code below will disable this security feature, by stops the MAC address from changing constantly but the wireless will work.
Add the following two lines of code to the end of 
`/etc/NetworkManager/NetworkManager.conf `
```bash 
[device]
wifi.scan-rand-mac-address=no
```
## Install LaTex
https://www.howtoinstall.co/en/ubuntu/xenial/texlive-latex-extra
     sudo apt-get update
     sudo apt-get install texlive-latex-extra

## install pandoc
    sudo apt-get install pandoc

## install node.js

``` bash
sudo apt-get install nodejs
```

https://stackoverflow.com/questions/13203335/set-node-js-to-path-ubuntu-12-04

Next you need to create a symbolic link from node to nodejs


``` bash
cd /usr/bin/
sudo ln -s nodejs node
```

Whenever needed, you can get rid if unneeded versions using 

    sudo apt autoremove
libxml2-dev is needed to install some r packages like readODS

    sudo apt-get install libxml2-dev
## Spotify for Linux: Instructions from Spotify.
1. Add the Spotify repository signing keys to be able to verify downloaded packages
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys BBEBDCB318AD50EC6865090613B00F1FD2C19886 0DF731E45CE24F27EEEB1450EFDC8610341D9410

2. Add the Spotify repository
    echo deb http://repository.spotify.com stable non-free | sudo tee /etc/apt/sources.list.d/spotify.list

3. Update list of available packages
    sudo apt-get update

4. Install Spotify
    sudo apt-get install spotify-client

## Install google chrome. 
This is needed because google chrome has flash. Firefox doesn't.  You can install flash in firefox, but what's the point.

https://askubuntu.com/questions/510056/how-to-install-google-chrome

``` bash
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'
sudo apt-get update
sudo apt-get install google-chrome-stable
```
## Install and Setup a video Player
https://askubuntu.com/questions/573948/simplescreenrecorder-error-missing-codecs
https://askubuntu.com/questions/387822/vlc-could-not-read-the-file-input-output-error
https://ubuntu-mate.community/t/vlc-not-playing-commercial-dvds/9687/4


The program `video_player` is already installed. 

## Get Hulu to work
https://askubuntu.com/questions/768493/problem-playing-online-videos-on-ubuntu-16-04


## Install Anaconda
Your PATH and PYTHONHOME variables will have to be modified.  
This is done by the anaconda installer to ~/.bashrc 
Here is the NTAWolf answer on 
    https://askubuntu.com/questions/505919/how-to-install-anaconda-on-ubuntu
Don't use sudo.  Install anacondo without using sudo. But the last step where the installer tries to prepend throws an error.  
```
CONTREPO=https://repo.continuum.io/archive/
# Stepwise filtering of the html at $CONTREPO
# Get the topmost line that matches our requirements, extract the file name.
ANACONDAURL=$(wget -q -O - $CONTREPO index.html | grep "Anaconda3-" | grep "Linux" | grep "86_64" | head -n 1 | cut -d \" -f 2)
wget -O ~/Downloads/anaconda.sh $CONTREPO$ANACONDAURL
bash ~/Downloads/anaconda.sh
```
close your terminal and open a new one to get the .bashrc code to run, or use load.
You will need to update after installation.  use `conda`  This is why you can't use sudo to insall.  `conda` doesn't work with sudo.
The not when you first load spyder tells you to use pip and the screen when spyder loads tells you not to use pip.  Use `conda` instead of pip.

https://github.com/spyder-ide/spyder/releases

```bash
conda update qt pyqt
conda update spyder
```
Now everything should be good.

## airfoil
https://www.lifewire.com/airfoil-5-toms-mac-software-4020889

https://askubuntu.com/questions/414737/how-do-i-install-itunes-on-ubuntu

## Remove PPA
https://askubuntu.com/questions/307/how-can-ppas-be-removed

## Add wine

https://wiki.winehq.org/Ubuntu
http://ubuntuhandbook.org/index.php/2015/12/install-wine-1-8-stable-new-ppa/

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo add-apt-repository ppa:ubuntu-wine/ppa

wget https://dl.winehq.org/wine-builds/Release.key
sudo apt-key add Release.key
sudo apt-add-repository 'https://dl.winehq.org/wine-builds/ubuntu/'

https://launchpad.net/~ubuntu-wine/+arcive/ubuntu/ppa

## install R 
https://anaconda.org/r/rstudio
https://conda.io/docs/user-guide/tasks/use-r-with-conda.html
if you have anaconda use
```
conda install r-essentials
conda install -c r rstudio
```
https://cran.r-project.org/bin/linux/ubuntu/README.html

It does not seem like you need to add a cran repository to `/etc/apt/sources.list`.
```bash
    sudo apt-get install r-base
    sudo apt-get install r-base-dev
```
```
sudo apt-get install -y libxml2-dev libcurl4-openssl-dev libssl-dev
```

Open Software & Updates and enable "Source code"
This allows you to build.
You can load package ess using:

    sudo apt-get build-dep ess 
add a key to your system
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9

sudo su - -c "R -e \"install.packages('Rccp', repos='http://cran.rstudio.com/')\""
sudo su - -c "R -e \"install.packages('htmltools', repos='http://cran.rstudio.com/')\""

Some of these might need to be tried more that once.


sudo su - -c "R -e \"install.packages('shiny', repos='http://cran.rstudio.com/')\""

sudo apt-get install -y default-jdk

sudo chmod 777 /usr/local/lib/R/site-library
sudo su  - -c "R -e \"install.packages(c('RJDBC','XLConnect','devtools','RJSONIO','sp','png','pixmap','mapdata','mpatools','maps','rgeos'),repos='http://cran.rstudio.com/')\""

sudo su - -c "R -e \"install.packages(c('RJDBC'),repos='http://cran.rstudio.com/')\""
sudo su - -c "R -e \"install.packages(c('XLConnect'),repos='http://cran.rstudio.com/')\""

sudo su - -c "R -e \"install.packages(c('devtools'),repos='http://cran.rstudio.com/')\""

sudo su - -c "R -e \"install.packages(c('RJSONIO'),repos='http://cran.rstudio.com/')\""

install r studio by point and click

install shinypt-get install -y default-jdk

## Install golang
`sudoapt-get install golang-go 




https://github.com/juhovh/shairplay

## SAS university edition
https://askubuntu.com/questions/367248/how-to-install-virtualbox-from-command-line
http://support.sas.com/software/products/university-edition/docs/en/SASUniversityEditionInstallGuideLinux.pdf
http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html

```bash
apt-get install virtualbox

https://stegard.net/2016/10/virtualbox-secure-boot-ubuntu-fail/

## to do
* Install hadoop
* Install spark
* Install Scala
* Install Java
* Install swift https://swift.org/download/#using-downloads
* install macoshttps://swift.org/download/#using-downloads
* install macos https://swift.org/download/#using-downloads
* install macos  http://www.makeuseof.com/tag/organized-desktop-rainmeter/
 https://github.com/geerlingguy/macos-virtualbox-vm
 search virtual macos
 
 
## fix the frozen mouse
https://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes

## Install Adobe Reader
sudo apt-get -y install acroread acroread-fonts
