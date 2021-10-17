# workstation-resources-linux
Using Ansible to set up the Linux development environment for ERoad API development.

First install Ansible on your local machine.

    $ sudo apt-add-repository -y ppa:ansible/ansible
    $ sudo apt-get update
    $ sudo apt-get install -y ansible

OK the fly in the ointment is that we have to download this as a ZIP first so that you can then install GIT.

Run the files

    aptInstall.yml - this installs most of the applications that need APT to be installed 
    snapInstalApps.yml - this uses SANP to install the applications (clue is in the name)
    dockerInstall.yml - uses APT but is big enough to be a separate script.

Don't run system.yml, it is where I am trying to work out getting system vars into the scripts dynamically.

I would start with the  

from the terminal run each of the files using the following command.
Ansible hosts is the file that points Ansible at the local machine, ask-become-pass asks for your password so that ansible can run SUDO, the password does not get recorded anywhere.


    ansible-playbook [FILE_INSTALL.yml] -i ansible_hosts.yml --ask-become-pass

Some of the scripts take a long time, or seem to. The IntelliJ script does take a while but then the SNAP installation process is really long too.
Another thing is the lack of feedback, frankly it is a bit disturbing at first and is why I split some of the scripts up a bit.


##Common issues
Or at least things that I found while running the  scripts.

###Failed to lock apt for exclusive operation
There seem to be several solutions and causes of this https://stackoverflow.com/questions/33563425/ansible-1-9-4-failed-to-lock-apt-for-exclusive-operation


###Ansible stuck on gathering facts
clean ~/.ansible directory and it may just work again, it did for me. I just emptied the ~/.ansible/tmp dir.

##Help
THere is lots of documentation on Ansible and it is a huge topic in itself.  
https://docs.ansible.com/  
https://www.middlewareinventory.com/blog/run-ansible-playbook-locally/


##Follow-up work
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

