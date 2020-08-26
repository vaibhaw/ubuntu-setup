[source](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository)

```sh
# update
sudo apt update

# install dependencies
sudo apt install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common

# install docker's GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

# add docker repository
sudo add-apt-repository \
    "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) stable"

# install docker engine and containerd
sudo apt install docker-ce docker-ce-cli containerd.io
```