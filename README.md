## For rapid deployment of common cloud-native tools

## create kubernetes
### 1. install hd
```
#!/usr/bin/env bash

ARCH=$(uname -m)
if [ ${ARCH} == 'x86_64' ]; then
  ARCH=amd64
elif [ ${ARCH} == 'armv6l' ]; then
  ARCH=arm6
elif [ ${ARCH} == 'armv7l' ]; then
  ARCH=arm7
elif [ ${ARCH} == 'arm64' ]; then
  ARCH=arm64
else
  echo "do not support ${ARCH}"
  echo "please feel free to help improve this at https://github.com/LinuxSuRen/tools/blob/master/install.sh"
  exit 1
fi

OS=$(uname -s)
if [ ${OS} == 'Darwin' ]; then
  OS=darwin
elif [ ${OS} == 'Linux' ]; then
  OS=linux
else
  echo "do not support ${OS}"
  echo "please feel free to help improve this at https://github.com/LinuxSuRen/tools/blob/master/install.sh"
  exit 2
fi

address=https://mirror.ghproxy.com/https://github.com/linuxsuren/http-downloader/releases/latest/download/hd-${OS}-${ARCH}.tar.gz

if [ -x "$(command -v curl)" ]; then
  curl -L $address | tar xzv hd
elif [ -x "$(command -v wget)" ]; then
  wget $address -O - | tar xzv hd
else
  echo "curl or wget is required to download hd."
  exit 3
fi

if ($(./hd version> /dev/null 2> /dev/null)); then
  sudo install hd /usr/bin/hd
  hd completion
  hd setup --proxy mirror.ghproxy.com --provider gitee
  hd fetch --reset
  echo "config the proxy with command: hd setup"
else
  echo "hd was not downloaded successfully."
fi
```
### 2. install required packages
```
hd setup --proxy mirror.ghproxy.com --provider gitee
hd fetch --reset
hd i chrony
hd i conntrack
hd i socat
hd i k9s
```
### 3. create k8s
```
export KKZONE=cn
kk create cluster
```