# workstation-resources-linux
Using Ansible to set up the Linux development environment for ERoad API development. 
 
OK the fly in the ointment is that we have to download this as a ZIP 
first so that you can then install GIT. 

First install Ansible on your local machine.

## Method A  
    $ sudo apt-add-repository -y ppa:ansible/ansible 
    $ sudo apt-get update 
    $ sudo apt-get install -y ansible 
 
## Method B  
Check if PIP is installed

    pip –version

If not installed Install pip for python 3

    sudo apt install python3-pip

Install Ansible via pi3

    pip install ansible

# Running the Ansible playbooks
So we are going to create all the project files pointing at localhost

Order of precedence
1. javaInstall.wml      - installs the JDK 8, 11 and Maven
2. snapInstallApps.yml  - installs intellij-idea-ultimate\community and slack
3. sublime-text4.yml    - sublime text 4
4. dockerInstall.yml    - docker installation
5. teamsInstall.yml     - MS teams 

Don't run system.yml, it is where I am trying to work out getting system vars into the scripts dynamically.
Change the snapInstallApps file to install the version of IntelliJ you want to use.

I would start with the from the terminal run each of the files using the following command.
Ansible hosts is the file that points Ansible at the local machine, ask-become-pass asks for your password so that ansible can run SUDO, the password does not get recorded anywhere.


    ansible-playbook [FILE_INSTALL.yml] -i ansible_hosts.yml --ask-become-pass

Some of the scripts take a long time, or seem to. The IntelliJ script does take a while but then the SNAP installation process is really long too.
Another thing is the lack of feedback, frankly it is a bit disturbing at first and is why I split some of the scripts up a bit.


## Common issues
Or at least things that I found while running the  scripts.

### Failed to lock apt for exclusive operation
There seem to be several solutions and causes of this https://stackoverflow.com/questions/33563425/ansible-1-9-4-failed-to-lock-apt-for-exclusive-operation


### Ansible stuck on gathering facts
clean ~/.ansible directory and it may just work again, it did for me. I just emptied the ~/.ansible/tmp dir.

## Help
THere is lots of documentation on Ansible and it is a huge topic in itself.  
https://docs.ansible.com/  
https://www.middlewareinventory.com/blog/run-ansible-playbook-locally/


## Follow-up work
I would like to add the following

    settings
    variables to remove the hard coding
    other applications like Teams
    packed apps like DEB and Zip files
    SQL Squirrel
    SOAP-UI
    Postmnm application.
    fortclient
    Chromebrowser

