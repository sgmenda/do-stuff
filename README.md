# do-stuff

### Setting up basic dev environment

```
apt-get update && apt-get -y upgrade
apt install -y aptitude
apt install -y vim tmux zsh git
apt install -y lld clang cmake build-essential python3 python3-dev
```

Create a user, give them sudo privileges, and allow SSHing in.
```
useradd --create-home --shell /bin/bash sanketh
passwd sanketh
usermod -aG sudo sanketh
ufw allow OpenSSH
ufw enable
ufw status
rsync --archive --chown=sanketh:sanketh ~/.ssh /home/sanketh
```

Setup user stuff
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
git clone https://github.com/sgmenda/dotfiles
ln -s dotfiles/dot-vimrc ~/.vimrc
ln -s dotfiles/dot-tmux.conf ~/.tmux.conf
```

oh-my-zsh theme: `norm` (to distinguish SSH session from my desktop.)

`:PluginInstall` on `vim` to install plugins.

### Setting up VNC

Install desktop environment and vncserver as in [this
article](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-18-04)

```
sudo apt install xfce4 xfce4-goodies xfce4-themes xfce4-terminal
sudo apt install tightvncserver
```

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

Also, it is easy to destroy a DO droplet and create a new one. It is hard to do
that with my laptop. Finally, I prefer developing stuff on Linux over MacOS.
