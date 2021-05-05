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

### Mount a remote location via SSH
##### Temporary
```
sudo apt-get install sshfs
sudo mkdir /mnt/<mount_point>
sudo chown <username> /mnt/<mount_point>
sudo chgrp <group_name> /mnt/<mount_point>
chmod go+x /mnt/<mount_point> # on WSL
sshfs -o default_permissions <ssh_location>:<path/to/folder> /mnt/<mount_point>
```
#### Make this mounting persistent (without editing `fstab`)
Add a cronjob for the same using `crontab -e` and adding the following job
```
@reboot sshfs -o default_permissions <ssh_location>:<path/to/folder> /mnt/<mount_point>
```
In WSL, cron doesn't start immediately. This is a problem. However, unlike most solutions on the web, we only want cron to work when we start WSL.
To set this straight, we need to allow `cron`  to run as sudo (it's a service afterall) but without bugging us for a password. To do so, do
```
sudo visudo
```
and add the following to it
```
# Allow cron to start without password
%sudo ALL=NOPASSWD: /etc/init.d/cron start
```
Now we can add a line to start cron to the `~/.bashrc` or `~/.zshrc` file. Twp points: 1. We should run it only if it isn't already running. 2. Placing it at the top will give it enough time to mount the remote drive by the time your shell is fully initialized.
```
service cron status | grep not && sudo /etc/init.d/cron start
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

### Changing starting directory for WSL in Windows Terminal
Add the following line to the `Ubuntu` entry in `Profile:list`:
```
"startingDirectory": "//wsl$/Ubuntu/home/<username>"
```
