# Things to do after installation of Ubuntu

## Fix the wireless router
    There seems to be a problem with my belkin usb wireless adapter.  
    https://askubuntu.com/questions/902992/ubuntu-gnome-17-04-wi-fi-not-working-mac-address-keeps-changing
	

```bash 
[device]
wifi.scan-rand-mac-address=no
```

    This stops the MAC address from changing constantly. The code below will disable this security feature, but the wireless will work.
    edit `/etc/NetworkManager/NetworkManager.conf`
    add the two lines:



## install pandoc
    sudo apt-get install pandoc

## Install emacs
    sudo apt-get install emacs
   
## install el-get to emacs
https://github.com/dimitri/el-get
First you can use lisp to clone the el-get github repository
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

 markdown-mode to emacs
https://stable.melpa.org/#/markdown-mode# 
``` Lisp
(require 'package)
(add-to-list 'package-archives
             '("melpa-stable" . "https://stable.melpa.org/packages/"))
(package-initialize)
```

## Install Mercurial
https://confluence.atlassian.com/get-started-with-bitbucket/mercurial-setup-860009660.html
sudo apt-get install mercurial

### clone vim-mode
hg clone https://bitbucket.org/lyro/vim-mode
https://www.emacswiki.org/emacs/VimMode

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
sudo apt-get install markdown

## Install preview mode
```emacs
   package-install markdown-preview-mode
```
## Install git
    sudo apt-get install git
## Install xclip
    sudo apt-get install xclip
# Set up the Github key.  See git hub instructions


Whenever needed, you can get rid if unneeded versions using 

    sudo apt autoremove
libxml2-dev is needed to install some r packages like readODS

    sudo apt-get install libxml2-dev
## Spotify for Linux: Instructions from Spotify.
### 1. Add the Spotify repository signing keys to be able to verify downloaded packages
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys BBEBDCB318AD50EC6865090613B00F1FD2C19886 0DF731E45CE24F27EEEB1450EFDC8610341D9410

### 2. Add the Spotify repository
    echo deb http://repository.spotify.com stable non-free | sudo tee /etc/apt/sources.list.d/spotify.list

### 3. Update list of available packages
    sudo apt-get update

### 4. Install Spotify
    sudo apt-get install spotify-client

## Install google chrome. 
This is needed because google chrome has flash. Firefox doesn't.  You can install flash in firefox, but what's the point.

https://askubuntu.com/questions/510056/how-to-install-google-chrome

    wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
    sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'
    sudo apt-get update
    sudo apt-get install google-chrome-stable

## Install Anaconda
Your PATH and PYTHONHOME variables will have to be modified.  
This is done by the anaconda installer to ~/.bashrc 
Here is the NTAWolf answer on 
    https://askubuntu.com/questions/505919/how-to-install-anaconda-on-ubuntu
```
CONTREPO=https://repo.continuum.io/archive/
# Stepwise filtering of the html at $CONTREPO
# Get the topmost line that matches our requirements, extract the file name.
ANACONDAURL=$(wget -q -O - $CONTREPO index.html | grep "Anaconda3-" | grep "Linux" | grep "86_64" | head -n 1 | cut -d \" -f 2)
wget -O ~/Downloads/anaconda.sh $CONTREPO$ANACONDAURL
bash ~/Downloads/anaconda.sh
```


## install R 
https://cran.r-project.org/bin/linux/ubuntu/README.html

It does not seem like you need to add a cran repository to `/etc/apt/sources.list`.
    sudo apt-get install r-base
    sudo apt-get install r-base-dev

Open Software & Updates and enable "Source code"
This allows you to build
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




