# Things to do after installation of Ubuntu/Lubuntu

This is a documentation of what I do after installing Lubuntu.  
After following the steps below, my disk showed 23.21 GiB used.

am currently using Lubuntu.  You could also use Ubuntu. to install, you need to go to the download site and also create a bootable usb key that
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
This is one way to install Lisp packages in emacs.  There are other ways, but this 
works well for me.

Go to https://github.com/dimitri/el-get and the section *The Lazy Installer*
Copy that into the *scratch* as indicated and run it.
Then go to the basic setup and copy that, as indicated, to the .emacs file.
If you don't copy to the .emacs file, then the packages you install 
will not reload after you exit and reenter emacs.

## Setup markdown mode to use pandoc

Pandoc can be used to view markdown.  Use 
    C-c C-c p
to request the preview.  The markdown command shown below 
will be run and call pandoc.


```{emacs}
;; pandoc-mode
(add-hook 'markdown-mode-hook 'pandoc-mode)
(setq markdown-command
      "pandoc -f markdown -t html -s --mathjax ")
```
## markdown-mode to emacs
This lets you edit markdown code for pushing to github.
If the pandoc command listed above works, you won't need this.
Inside emacs use 

```emacs
el-get-install markdown-mode
```

## install node.js
This is needed for the emacs pluging livedown (listed next) to work.

``` bash
sudo apt-get install nodejs
sudo apt-get install npm
npm install -g livedown
```

## install livedown.
https://github.com/shime/livedown
Livedown is a usefull way to view markdown.  It requires nodejs and npm.
The advantage of livedown over using pandoc is that when you save a md file,
livedown will show the results immediately.  
Inside emacs, use: 

```
el-get-install livedown
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
Use `conda` instead of pip.  The code is shown below 

https://github.com/spyder-ide/spyder/releases

```bash
conda update qt pyqt
conda update spyder
```

## Install Tensorflow

Read this before you install tensorflow.

https://www.tensorflow.org/install/install_linux

```bash
conda install tensorflow
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
## Install R 

rstudio to create pdf documents

https://help.ubuntu.com/community/LaTeX


```bash
sudo apt-get update
sudo apt-get install texlive-full
```

```bash
sudo apt-get install libcurl4-openssl-dev 
sudo apt-get install libxml2-dev
sudo apt-get install libssl-dev

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

## install node.js
This is needed for the emacs pluging livedown (listed next) to work.

``` bash
sudo apt-get install nodejs
sudo apt-get install npm
npm install -g livedown
```

## install livedown.
https://github.com/shime/livedown
This is whay nodejs and npm was installed earlier.
Inside emacs, use: 

```
el-get install livedown
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

## Install Tensorflow

Read this before you install tensorflow.

https://www.tensorflow.org/install/install_linux

```bash
conda install tensorflow
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
## Install R 
http://cran.cnr.berkeley.edu/


After you follow the berkeley directions, not that you can do this

```bash
sudo apt-get install r-cran-*
```

It will save you a ton of time.


## Install Rstudio
https://www.rstudio.com/products/rstudio/download/#download

## install R the Conda Way (recommend not doing this but installing r with apt-get)
https://anaconda.org/r/rstudio
https://conda.io/docs/user-guide/tasks/use-r-with-conda.html

Use anaconda:

Make sure you are in an environment first, even if it is the root.

```
source activate root
```


```bash
conda install r-essentials
conda install rstudio
```

As soon as you install r  and rstudio, you need to start up rstudio and
the try to install that package that you love and no one else knows about.
This will test to see if your system is set up to install obscure packages with
dependencies.  

I use the gk package.  Packages are installed inside r with 

```bash
install.packages()
```

You can also use conda with

```bash
conda install r-ggplot2
```

Many times if a package will not install because of dependencies, you can 
still use conda to install the package. 
Here is an example installation.
Conda looks for binaries that are available.  
There is nothing for r-gk so I have to use 

```bash
install.packages()
```

However this produced and error message about gnu-gcc and the package didn't install.
This stackoverflow had the answer:

https://stackoverflow.com/questions/46450912/unable-to-execute-x86-64-conda-cos6-linux-gnu-gcc-no-such-file-or-directory

The comment by 

https://stackoverflow.com/users/3257826/ray-donnelly
is to use:

```bash
conda create -n renv r-essentials=1.7.0 gcc_linux-64
source activate renv
```

There is another user

https://stackoverflow.com/users/1170370/msarahan

who mentioned that activation sets a bunch of important variables
so even if you don't have a bunch of environments, it is still 
a good idea to active.

```
source activate root
```
I was able to get rstudio running in the renv above and get the gk 
package to install.  A combination of the two answers would indicate
that I only needed to install gcc_linux-64 into the root environment.
I avoid using a version number on packages becuase the default would be the
latest one.   If you are worried about versioning, you can have conda 
environments with the exact versions of packages you need.  But I would 
suggest that if you are worried about what version of a package is needed to
make sure your code works and isn't brocken by some update then use Microsoft R Open.
The whole point of MRO is to limit the frequency of updates to ensure that new versions
don't break things.  I don't like it because I want the latest, but if you are worried about
thing breaking, use MRO. Also RevolutionR was bought by MS and their guys are most likely the 
ones managing it.  That is a plus.  I recommend having at least one environment where MRO is 
used. 

https://conda.io/docs/user-guide/tasks/use-mro-with-conda.html



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

## spotify
http://howtoubuntu.org/how-to-install-spotify-in-ubuntu

```bash
sudo apt-add-repository -y "deb http://repository.spotify.com stable non-free" &&
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D2C19886 &&
sudo apt-get update -qq &&
sudo apt-get install spotify-client
```


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
 
 
