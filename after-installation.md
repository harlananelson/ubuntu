# Things to do after installation of Ubuntu/Lubuntu
This is a documentation of what I do after installing Lubuntu.  
After following the steps below, my disk showed 23.21 GiB used.

I am currently using Lubuntu.  You could also use Ubuntu. to install, you need to go to the download site and also create a bootable usb key that
you will use for the installation. That's easy. This document shows you what to do afterwards.

## Install xclip
This program will let you copy your public key to the buffer.  It is needed when you upload your git key to gihub. 
It is also lets you paste into the terminal using <shift> <insert>

```bash
    sudo apt-get install xclip
```

## Install git

```bash
    sudo apt-get install git
```

## Set up the Github key.  See git hub instructions
https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/

You might want to save the passcode so you don't have to keep entering it.
https://stackoverflow.com/questions/21095054/ssh-key-still-asking-for-password-and-passphrase

```bash
ssh-add -k ~/.ssh/id_rsa
```

## Install LaTeX
You will need this in rstudio to create pdf documents

https://help.ubuntu.com/community/LaTeX


```bash
sudo apt-get update
sudo apt-get install texlive-full
```

## install pandoc
Pandoc is also used for document conversion.

```bash
sudo apt-get install pandoc
```

## Install emacs
If you don't use emacs, skip this step.

```bash
sudo apt-get install emacs
```
   
## install el-get for emacs
https://github.com/dimitri/el-get
This will be the way Lisp packages are installed.

Go to https://github.com/dimitri/el-get and the section *The Lazy Installer*
Copy that into the *scratch* as indicated and run it.
Then go to the basic setup and copy that, as indicated, to the .emacs file.
If you don't copy to the .emacs file, then the packages you install 
will not reload after you exit and reenter emacs.

## markdown-mode to emacs
This lets you edit markdown code for pushing to github.
Inside emacs use 

```emacs
el-get-install markdown-mode
```

## Install Anaconda
    https://askubuntu.com/questions/505919/how-to-install-anaconda-on-ubuntu
Don't use sudo.  Install anacondo without using sudo.as 

```
    CONTREPO=https://repo.continuum.io/archive/
    # Stepwise filtering of the html at $CONTREPO
    # Get the topmost line that matches our requirements, extract the file name.
    ANACONDAURL=$(wget -q -O - $CONTREPO index.html | grep "Anaconda3-" | grep "Linux" | grep "86_64" | head -n 1 | cut -d \" -f 2)
    wget -O ~/Downloads/anaconda.sh $CONTREPO$ANACONDAURL
    bash ~/Downloads/anaconda.sh
```

Close your terminal and open a new one to get the .bashrc code to run, or use load.

You will need to update spyder after installation.  Use `conda`  This is why you can't use sudo to insall.  `conda` doesn't work with sudo.
The note when you first load spyder tells you to use pip and the screen, when spyder loads, tells you not to use pip.  
Use `conda` instead of pip.

https://github.com/spyder-ide/spyder/releases

```bash
conda update qt pyqt
conda update spyder
```
## Install Some Office Tools
###LibreOffice
If you are using Ubuntu, you have this already.

```bash
sudo apt-get install libreoffice
```
## Use VIM as your default editor 

```bash
export VISUAL=vim
export EDITOR="$VISUAL"
```

## Fix errors
https://www.raspberrypi.org/forums/viewtopic.php?t=196070

There is a problem running python from the command line. It might get fixed,
but the works for now.

```bash
sudo apt-get install at-spi2-core
```

## install R 
https://anaconda.org/r/rstudio
https://conda.io/docs/user-guide/tasks/use-r-with-conda.html

Use anaconda:

```bash
conda install r-essentials
conda install -c r rstudio
```

## Install golang

https://github.com/juhovh/shairplay


```bash
sudoapt-get install golang-go 
```


## SAS university edition
https://askubuntu.com/questions/367248/how-to-install-virtualbox-from-command-line
http://support.sas.com/software/products/university-edition/docs/en/SASUniversityEditionInstallGuideLinux.pdf
http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html

```bash
apt-get install virtualbox
```
https://stegard.net/2016/10/virtualbox-secure-boot-ubuntu-fail/


## Remove old unused packages
Whenever needed, you can get rid if unneeded versions using 

    sudo apt autoremove


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
 
 
