# How to set up Linux on Windows 10

In this repository, I will provide a guide to setting up a Windows Subsystem for Linux (WSL),
installing the Anaconda Python distribution, as well as accessing common Python editors such as Jupyter Lab.

## Install WSL

1. Before installing any Linux distributions on Windows, enable the "Windows Subsystem for Linux" feature. Open PowerShell as Administrator (right click on the Powershell icon and select "Run as Administrator") and run: 

	```dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart``` 
	
	to installs WSL 1. 

2. You can choose to update to WSL 2 if your Windows system is version 2004 build 19041 or higher. Read more about their difference [here](https://docs.microsoft.com/en-us/windows/wsl/compare-versions). If you do not wish to update, jump to Step 3. To update to WSL 2, restart your machine and open PowerSell as Administrator. Run 

	```dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart``` 
	
	to enable "Virtual Machine Platform" feature. Run 
	
	```wsl --set-default-version 2``` 
	
	to set WSL 2 as the default version.

3. Restart your machine and install your Linux distribution of choice from the Microsoft Store. This guide uses Ubuntu 20.04 LTS, see other guides such as [this](https://www.digitalocean.com/community/tutorials/how-to-install-python-3-and-set-up-a-programming-environment-on-an-ubuntu-20-04-server) if you are installing other distributions.

4. Troubleshoot your installation with information on the Microsoft documentation [here](https://docs.microsoft.com/en-us/windows/wsl/install-win10#troubleshooting-installation)

## Install Python3 on Ubuntu 20.04

1. After installing the Linux distribution, you will be asked to create a Username and Password. If you forgot your password, you can follow [this tutorial](https://docs.microsoft.com/en-us/windows/wsl/user-support#forgot-your-password) to retrieve it. 

2. Check that your version is up-to-date by running (don't type the $ sign):

	```
	$ sudo apt update
	$ sudo apt -y upgrade
	```
	The ```-y``` flag indicates that you are agreeing to all prompts.

3. Once the installation is complete, you can check your Python3 version by running:

	```$ python3 -V```

4. Install pip to install and manage packages by running:

	```$ sudo apt install -y python3-pip ```

	After which you can install Python packages by running:
	
	```$ pip3 install package_name```
	
5. There are a few more packages that you could install that would be useful:
	
	```$ sudo apt install -y build-essential checkinstall libssl-dev libffi-dev python3-dev```

6. For some reason, the default Node.js version on Ubuntu is always really low. You can check you Node.js version by running:
	
	```$ node -v```
	
	, it is likely 0.something. Node.js is necessary to get Jupyter Lab working correctly so let's update it with the Node Version Manager([nvm](https://github.com/nvm-sh/nvm)). Install nvm by running:
	
	```$ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.35.1/install.sh | bash```
	
	Restart the Ubuntu terminal and check that the installation is successful by running:
	
	```$ nvm --version```
	
	and get the version. Check the available Node.js releases using:
	
	```$ nvm ls-remote```
	
	Choose your version and install it with:
	
	```$ nvm install version.number```

## Install Anaconda

1. You can download the Anaconda installer anywhere you want but I was recommended the "tmp" folder. You can find it by moving up a few levels of directory using ```$ cd ..```. Us ```$ ls``` to check that you have found "tmp" and use ```$ cd tmp``` to relocate yourself there.

2. Go to the Anaconda website to copy the installer link and run:

	```$ curl https://repo.anaconda.com/archive/Anaconda3-2020.02-Linux-x86_64.sh --output anaconda.sh```
	
	changing the web address to the one you found (more up-to-date).
	
3. You can verify the integrity of the installer by running:

	```$ sha256sum anaconda.sh```
	
	to receive an output in the form:
	
	```$ 2b9f088b2022edb474915d9f69a803d6449d5fdb4c303041f60ac4aefcc208bb  anaconda.sh```
	
	Check your output with [this page](https://docs.anaconda.com/anaconda/install/hashes/lin-3-64/).
	
4. Now run the script:

	```$ bash anaconda.sh```
	
	and follow the installation prompts.

5. After the installation completes, activate the installation by sourcing the ```~/.bashrc``` file:
	
	```$ source ~/.bashrc```
	
	You will now see a ```(base)``` before your username.

6. You can add environments following [this tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-the-anaconda-python-distribution-on-ubuntu-20-04)

## Accessing Jupyter Lab

1. Install Jupyter Lab by running:

	```$ conda install -c conda-forge jupyterlab```
	
2. Run 

	```$ jupyter lab --no-browser```

3. Copy the url generated to your browser and voila!

4. Close the session by clicking ```Ctrl+C``` twice.
