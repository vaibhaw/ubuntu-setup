Inspired by:

- [MacOS Setup Guide by Sourabh Bajaj](https://sourabhbajaj.com/mac-setup/) [github](https://github.com/sb2nov/mac-setup)
- [Ubuntu on Steroids](https://github.com/utkuufuk/ubuntu-on-steroids)

### Social 

#### Connect Microsoft Exchange Account
user: email; domain: outlook.office365.com


#### Mailspring
```
sudo snap install mailspring
```
Remove signature which says Sent from MailSpring


#### Install thunderbird & libreoffice
```
sudo apt install thunderbird
sudo apt install libreoffice # will also install fonts Carlito and Caladea
```

#### Customize Thunderbird
Add email to thunderbird

 - Alt+V; View -> Layout -> Show Menu Bar
 - View -> Sort By -> Date, Descending, Threaded
 - Edit -> Preferences -> Display -> Font -> Carlito, Size -> 11

> Carlito is metrically compatible font with Calibri. Similarly, Caladea is for Cambria

 - Edit -> Preferences -> Composition -> Font -> Variable Width, Size -> Medium

#### Customize terminal

- Hamburger Menu -> Preferences
- Theme -> Dark
- Profiles -> Unnamed -> Colors -> Text & Background Color -> Solarized Dark, Palette -> Tango/Solarized Dark

#### Microsoft Teams
Download and install from [here](https://www.microsoft.com/en-ca/microsoft-365/microsoft-teams/download-app#desktopAppDownloadregion)
It will also setup an apt repository

> command line version
```
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/ms-teams stable main" > /etc/apt/sources.list.d/teams.list'

sudo apt update
sudo apt install teams
```

### Install Browsers

#### Google Chrome
Download and install from [here](https://www.google.com/intl/en/chrome/)
It will also setup an apt repository

> command line version
```
wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
sudo apt update
sudo apt install google-chrome-stable
# sudo apt install google-chrome-beta
```

#### Mozilla Firefox
Preferences -> General -> Restore previous session
Preferences -> General -> Warn you when quitting the browser

Preferences -> General -> Download -> Always ask you where to save files

### Build tools and other general dependencies


#### Common Dependencies
```
sudo apt install net-tools
sudo apt install curl
# ensure apt is set up to work with https sources
sudo apt install apt-transport-https ca-certificates gnupg

sudo apt install git
```

#### Build Tools
```
sudo apt install build-essential
sudo apt install gcc g++ make
```

### IDEs

#### VSCode, Sublime, PyCharm CE, IDEA CE, Postman, Neovim
```
sudo snap install code --classic
sudo snap install intellij-idea-community --classic 
sudo snap install pycharm-community --classic
sudo snap install postman

# Sublime: can also be installed using snap but not published by Sublime
# Install the GPG key
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
# select channel stable. replace stable with dev to use the dev channel
echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list

sudo apt update
sudo apt install sublime-text

sudo apt install neovim
```

#### Configure Sublime
CTRL+SHIFT+P -> Install Package Control
Install Package
- Pretty JSON

#### [Snap cheatsheet](https://snapcraft.io/docs/getting-started)
```
# just list the refreshed packages
snap refresh --list 
# update all of them
sudo snap refresh   
# update just one
sudo snap refresh vlc

# find package
snap find vlc
# more about package
snap info package_name

# list installed snaps
snap list

# install the bleeding edge version
sudo snap install --channel=edge vlc

# switch channel after the installation
 sudo snap switch --channel=edge vlc
```

### Cloud Tools

#### aws-cli
```
sudo snap install aws-cli --classic
```

#### GCP SDK [source](https://cloud.google.com/sdk/docs/downloads-apt-get) 
use snap
```
snap install google-cloud-sdk --classic
```

use apt
```
# add key
curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key --keyring /usr/share/keyrings/cloud.google.gpg add -

# add source
echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | sudo tee -a /etc/apt/sources.list.d/google-cloud-sdk.list

sudo apt update
sudo apt install google-cloud-sdk

# config
gcloud init
```

### Install Programming Languages

#### Java
JDK from Oracle's OpenJDK

JDK from AdoptOpenJDK. AdoptOpenJDK is supported by Azul, IBM, Ocado, and Microsoft. They started because Oracle messed up with licensing of JDK for enterprise. [more](https://developer.ibm.com/technologies/java/blogs/adoptopenjdk-an-open-java-distribution-and-community-you-can-count-on/)


Builds are available for OpenJ9 (IBM’s JVM) and HotSpot (Oracle's JVM). [more](https://medium.com/adoptopenjdk/adoptopenjdk-rpm-and-deb-files-7003ba38144e)
What is OpenJ9? According to the AdoptOpenJDK website, OpenJ9 is a JVM that is designed for low memory usage and fast start-up time. 
```
wget -qO - https://adoptopenjdk.jfrog.io/adoptopenjdk/api/gpg/key/public | sudo apt-key add -
sudo add-apt-repository --yes https://adoptopenjdk.jfrog.io/adoptopenjdk/deb/
apt-get update # update if you haven't already
apt-get install adoptopenjdk-11-hotspot
```


#### Python
Python packaged with Ubuntu comes pre-installed. Install pip OS shipped python
```
sudo apt install python3-pip
```

Python from Anaconda distribution

Anaconda dependencies to run GUI packages
```
sudo apt install libgl1-mesa-glx libegl1-mesa libxrandr2 libxrandr2 libxss1 libxcursor1 libxcomposite1 libasound2 libxi6 libxtst6
```


Download and install anaconda
```
wget https://repo.anaconda.com/archive/Anaconda3-2020.02-Linux-x86_64.sh
bash Anaconda3-2020.02-Linux-x86_64.sh

# accept default location
# say yes to run conda init

# make run conda init
source ~/.bashrc

# disable conda's base env activation during startup
conda config --set auto_activate_base false
```

#### Go [more](https://github.com/golang/go/wiki/Ubuntu)

```
# install go (only on Ubuntu 20.04)
sudo apt install golang-1.14-go
# add go/bin to path
echo 'export PATH=$PATH:/usr/lib/go-1.14/bin/go' >> ~/.bashrc
```

#### Node.js [more](https://github.com/nodesource/distributions/blob/master/README.md#debinstall)

```
# Current is v14.x. Use lts instead of current for LTS which is v12.x
curl -sL https://deb.nodesource.com/setup_current.x | sudo -E bash -
sudo apt install -y nodejs
```

#### Yarn package manager
```
curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt update && sudo apt install yarn

```

### Tools

#### Archiving/Unarchiving
```
sudo apt install p7zip-full p7zip-rar
```


#### Rclone
```
# Install rclone
curl https://rclone.org/install.sh | sudo bash
```

### SSH Keys



### GPG Keys

 - [generate](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-gpg-key)
 - [export/import](https://www.debuntu.org/how-to-importexport-gpg-key-pair/)


 sudo apt install tmux
 sudo apt install byobu



To make locate and updatedb work
```sh
sudo apt install mlocate
```

### Image Editors
```sh
sudo apt install shotwell
```

### Customizations
```sh
sudo apt install gnome-tweak-tool

```

### Video
Kazam
```sh
sudo apt install ubuntu-restricted-extras
sudo apt install kazam
sudo apt install vlc
```


### ZSH and Oh-my-zsh
```sh
sudo apt install zsh
```

```sh
# oh my zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# powerline fonts
sudo apt install fonts-powerline
```

