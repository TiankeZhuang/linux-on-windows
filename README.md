# How to set up Linux on Windows 10

In this repository, I will provide a guide to setting up a Windows Subsystem for Linux (WSL),
installing the Anaconda Python distribution, as well as accessing common Python editors such as Jupyter Lab.

## Install WSL

Before installing any Linux distributions on Windows, enable the "Windows Subsystem for Linux" feature:

Open PowerShell as Administrator (Right click on the Powershell icon and select "Run as Administrator") and run:

```dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart```

to installs WSL 1. Restart your machine and install your Linux distribution of choice in the Microsoft Store
