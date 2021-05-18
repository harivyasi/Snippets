# Windows Terminal settings

## Entries in the `settings.json` file
Remember to fill in unique GUIDs, update <username> and check all the paths. New GUIDs can be created [here](https://www.guidgenerator.com).
```
{
    "defaultProfile": "{}",
    "profiles": 
    {
        "defaults": {},
        "list": 
        [
            {
                "commandline": "powershell.exe",
                "guid": "{}",
                "hidden": true,
                "name": "Windows PowerShell"
            },
            {
                "commandline": "cmd.exe",
                "guid": "{}",
                "hidden": false,
                "name": "Command Prompt"
            },
            {
                "guid": "{}",
                "hidden": false,
                "name": "PowerShell",
                "source": "Windows.Terminal.PowershellCore"
            },
            {
                "guid": "{}",
                "hidden": false,
                "name": "Ubuntu",
                "source": "Windows.Terminal.Wsl",
                "startingDirectory": "//wsl$/Ubuntu/home/<username>"
            },
            {
                "guid": "{}",
                "hidden": true,
                "name": "Azure Cloud Shell",
                "source": "Windows.Terminal.Azure"
            },
            {
                "commandline": "\"C:\\Program Files\\Git\\git-cmd.exe\" --cd-to-home",
                "icon": "C:\\Program Files\\Git\\mingw64\\share\\git\\git-for-windows.ico",
                "name": "Git CMD",
                "tabTitle": "Git CMD"
            },
            {
                "bellStyle": "none",
                "commandline": "\"C:\\Program Files\\Git\\bin\\bash.exe\" --cd-to-home --login",
                "icon": "C:\\Program Files\\Git\\mingw64\\share\\git\\git-for-windows.ico",
                "name": "Git Bash",
                "tabTitle": "Git Bash"
            },
            {
                "guid": "{}",
                "name": "Miniconda",
                "commandline": "cmd.exe \"/K\" C:\\Program Files\\miniconda3\\Scripts\\activate.bat C:\\Program Files\\miniconda3",
            }
        ]
    }
}
```