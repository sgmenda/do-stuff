# do-stuff

### Setting up basic dev environment

```
apt-get update && apt-get -y upgrade
apt install -y aptitude
apt install -y vim tmux zsh git
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
git clone https://github.com/sgmenda/dotfiles
ln -s dotfiles/dot-vimrc ~/.vimrc
ln -s dotfiles/dot-tmux.conf ~/.tmux.conf
apt install -y lld clang cmake build-essential
```

Create a user and give them sudo privileges
```
adduser sanketh
usermod -aG sudo sanketh
```

oh-my-zsh theme: `norm` (to distinguish SSH session from my desktop.)

`:PluginInstal` on `vim` to install plugins.

### Setting up VNC

Follow
[How to Install and Configure VNC on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-18-04)

### On VM

To start server
```
vncserver -geometry 1600x1200
```
To kill vncserver
```
vncserver -kill :1
```

To set password
```
vncpasswd
```

### On local machine

Port forwarding
```
ssh -L 5901:127.0.0.1:5901 -C -N -l root $DO_IP
```

To open VNC
```
open vnc://localhost:5901
```

## Why I am doing this?

I wanna work on firefox, but I don't have a powerful laptop. This allows me to
use DO to work on firefox.
