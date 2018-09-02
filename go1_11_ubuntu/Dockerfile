# dev command `docker run -it --rm ubuntu:bionic /bin/sh`
FROM ubuntu:bionic
ARG GO_VERSION="1.11"
SHELL ["/bin/bash", "-c"]
RUN cd ~/ && mkdir -p ~/go && \
echo "export GOPATH=$HOME/go" >> ~/.profile && \
echo "export PATH=$PATH:$GOPATH/bin" >> ~/.profile && \
source ~/.profile && \
apt-get update && \
apt-get install -y apt-utils && \
apt-get install -y curl git mercurial make binutils bison gcc build-essential apt-utils golang && \
bash < <(curl -s -S -L https://raw.githubusercontent.com/moovweb/gvm/master/binscripts/gvm-installer) && \
source /root/.gvm/scripts/gvm && \
gvm install go${GO_VERSION} && \
gvm use go${GO_VERSION} --default
# mkdir -p /root/.gvm/pkgsets/go1.11/global/src/