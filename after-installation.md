# Things to do after installation
* There seems to be a problem with my belkin usb wireless adapter.  
https://askubuntu.com/questions/902992/ubuntu-gnome-17-04-wi-fi-not-working-mac-address-keeps-changing
This stops the MAC address from changing constantly. The code below will disble this security feature, but the wireless will work.
edit `/etc/NetworkManager/NetworkManager.conf`
add the two lines:
`[device]
wifi.scan-rand-mac-address=no`

Whenever needed, you can get rid if unneeded versions using 

    sudo apt autoremove
libxml2-dev is need to install some r packages like readODS

    sudo apt-get install libxml2-dev```
## Install emacs
    sudo apt-get install emacs
## Install git
    sudo apt-get install git
## Install xclip
    sudo apt-get install xclip
# Set up the Github key.  See git hub instructions

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

    wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-
    sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'
    sudo apt-get update
    sudo apt-get install google-chrome-stable





