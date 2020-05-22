# How to set up Linux on Windows 10

In this repository, I will provide a guide to setting up a Windows Subsystem for Linux (WSL),
installing the Anaconda Python distribution, as well as accessing common Python editors such as Jupyter Lab.

## Install WSL

1. Before installing any Linux distributions on Windows, enable the "Windows Subsystem for Linux" feature. Open PowerShell as Administrator (right click on the Powershell icon and select "Run as Administrator") and run: ```dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart``` to installs WSL 1. 

2. You can choose to update to WSL 2 if your Windows system is version 2004 build 19041 or higher. Read more about their difference [here](https://docs.microsoft.com/en-us/windows/wsl/compare-versions). If you do not wish to update, jump to Step 3. To update to WSL 2, restart your machine and open PowerSell as Administrator. Run ```dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart``` to enable "Virtual Machine Platform" feature. Run ```wsl --set-default-version 2``` to set WSL 2 as the default version

3. Restart your machine and install your Linux distribution of choice from the Microsoft Store. This guide uses Ubuntu 20.04 LTS, but other distributions would work in similar fashion.
