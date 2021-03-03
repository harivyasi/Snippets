# (Ubuntu) Linux

## Configuration

### Create new user with given `gid` and `uid` and make them `sudo`er
```
sudo groupadd --gid XXX <group_name>
sudo adduser --uid YYYYYY --gid XXX <username>
sudo usermod -aG sudo <username>
```

### Change default user in WSL
In Powershell:
```
ubuntu config --default-user <username>
```

### Updates after first start of shell
```
sudo apt update && sudo apt upgrade
```

### Temporarily mount a remote location via SSH
```
sudo apt-get install sshfs
sudo mkdir /mnt/<mount_point>
sudo chown <username> <mount_point>
sudo chgrp <group_name> <mount_point>
sshfs -o default_permissions <ssh_location>:<path/to/folder> /mnt/<mount_point>
```

### Install `zsh` and `omyzsh` with theme `p10k`
Instruction: Install line by line
```
sudo apt install zsh
```
```
sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```
```
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```
```
sed -i "s/$(grep ZSH_THEME .zshrc | grep -Z "^[^#]")/ZSH_THEME=\"powerlevel10k\/powerlevel10k\"/g" .zshrc
```
```
chsh -s /usr/bin/zsh
```