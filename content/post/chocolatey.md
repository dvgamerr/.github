+++
title = "Chocolatey recommend software for developer"
description = "Chocolatey recommend software for developer"
tags = [
    "chocolatey",
    "powershell",
    "shell"
]
date = 2019-01-03T06:21:31Z
author = "Kananek T."
+++

1. Install chocolatey with `cmd as administrator` and run command below.

```bash
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```

2. exit terminal and run `cmd as administrator` again

```bash
@echo off
choco feature enable -n allowGlobalConfirmation

choco install virtualbox --version=6.0.14
choco install git.install --params "/NoGuiHereIntegratio /NoShellHereIntegration /NoShellIntegration" --force

# Tool Recommand
choco install aegisub azure-cli cmder curl deno ^
ffmpeg flutter forticlientvpn github-desktop golang googlechrome ^
hugo k9s kubeless kubernetes-cli kubernetes-helm kubernetes-kompose ^
microsoft-teams mkvtoolnix mpc-hc mremoteng ngrok.portable nvm ^
obs-studio postman powershell-core putty.install python2 python3 ^
robo3t sonarqube-scanner.portable sourcetree sql-server-management-studio ^
tableplus telegram vscode winrar winscp

# LINE pc Install with command
curl --silent https://desktop.line-scdn.net/win/new/LineInst.exe -o %TEMP%/LineInst.exe >nul %TEMP%/LineInst.exe
```
