Vagrant, Ansible, and VirtualBox on WSL (Windows Subsystem for Linux) 

How To

This guide covers how to get Vagrant and Ansible running together on Windows 10 using WSL (Windows Subsystem for Linux), such that they use VirtualBox on the Windows host.

Action Steps
Install Git on Windows
1. Go to https://git-scm.com/download/win.
2. Download 64-bit Git for Windows.
3. Run the .exe file once it finishes downloading.

Install VirtualBox on Windows
1. Go to https://www.virtualbox.org/wiki/Downloads.
2. Click on Windows Hosts link.
3. Run the .exe file once it finishes downloading.
4. (Optional) Download and install the Extension Pack.

Install WSL on Windows 10 Pro
1. Open PowerShell as Administrator and run: Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows Subsystem-Linux


Action 
Steps 2. Restart Windows.

Install Ubuntu 18.04 LTS from Windows Store
1. Go to https://www.microsoft.com/en-us/p/ubuntu-1804lts/9n9tngvndl3q#activetab=pivot:overviewtab.
2. Click the Get / Install option.
3. Run Ubuntu 18.04 from the Start menu.
4. Create a username and password when prompted.
5. Close the Ubuntu terminal window.

Configure VS Code to use WSL in the Integrated Terminal
1. Press Ctrl+Shift+P to open the Command Palette.
2. Type: Terminal: Select Default Shell
3. Select: WSL Bash

Install Python and PIP in WSL
1. Press Ctrl+` in VS Code to open the Integrated Terminal.
2. Type the following in the terminal: cd ~ sudo apt-get update sudo apt-get dist-upgrade -y sudo apt-get install python mkdir downloads cd downloads curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py python get-pip.py --user
3. Add the local bin directory to PATH: echo 'export PATH="${PATH}:/home/jeff/.local/bin"' >> ~/.bashrc Note: Replace jeff with your actual username.

Install Ansible in WSL
1. Type the following in the terminal: pip install ansible --user

Action Steps
Install Vagrant in WSL
1. Go to https://www.vagrantup.com/downloads.html.
2. Right-click and copy the link for the 64-bit Debian package.
3. Type the following in the terminal: wget https://releases.hashicorp.com/vagrant/2.1.5/vagrant_2.1.5_x86_64.deb dpkg -i vagrant_2.1.5_x86_64.deb Note: Replace the link and the .deb package name with the one you actually copied.

Configure Vagrant in WSL to Use VirtualBox on Windows
1. Type the following in the terminal: echo 'export VAGRANT_WSL_ENABLE_WINDOWS_ACCESS="1"' >> ~/.bashrc echo 'export PATH="${PATH}:/mnt/c/Program Files/Oracle/VirtualBox"' >> ~/.bashrc source ~/.bashrc
Clone my Demo GitHub Repository
1. Type the following in the terminal: cd /mnt/c/Users/jeff/Desktop/ git clone https://github.com/JeffReeves/WSL-Ansible-VagrantVirtualBox.git cd WSL-Ansible-Vagrant-VirtualBox
Start the VM in VirtualBox using Vagrant
1. Type the following in the terminal: vagrant up
Verify VM was Provisioned
1. Go to http://127.0.0.1:8080/ in a browser.
2. Verify that a demo page is displayed.
Stop and Destroy the VM
1. Type the following in the terminal: vagrant halt vagrant destroy
