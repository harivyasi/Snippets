# Windows

## Configuring ssh
Assuming that OpenSSH was installed using Windows Features, the configuration folder is `$HOME\.ssh`.
In this folder make a file called `config` that is supposed to be similar to that for Linux. However, to make it work with a proxy server, you need to configure it like as follows:
```
Host Jumper
  HostName jumper.server.com
  User <username>

Host RemoteComputer
  ProxyCommand C:\Windows\System32\OpenSSH\ssh.exe -W %h:%p Jumper
  HostName target.server.com
  User <username>
```
