# **Ansible Development Environment Setup**

This Ansible playbook is a demo to showcase the potential use of infrastructure as code to provision servers within the intodata group. 

### **Features**

This Ansible playbook performs the following essential tasks:

Keeping Apt Packages Up to Date: Ensure your system is up to date by updating and upgrading apt packages.

Creating a New User: Enhance security and control by creating a new user and assigning and assigning the appropriate privileges.

Install required packages

Update security congiruation: disable password login for root user using ssh. 


## **Requirements**

- [Ubuntu](https://www.ubuntu.com) or [Debian](https://www.debian.org) Linux
- Bash shell
- [Ansible](https://www.ansible.com) 2.8 or newer
- [Python](https://www.python.org/) 3.7 or newer as required by Ansible

### Ubuntu

This Ansible Playbook has been tested on the following Linux releases:

-  [Ubuntu 22.04.2 LTS](https://ubuntu.com/blog/ubuntu-22-04-lts-whats-new-linux-desktop)

### Ubuntu on WSL

I've used this playbook to install packages on Ubuntu running on [[Windows Subsystem for Linux]] on Windows 11.

## **Installation Instructions**

To run the playbook, ensure that you have the latest version of Ansible installed. Please follow the steps below:

###  Installing Ansible

Ansible is an agentless automation tool that you install on a single host (referred to as the control node). From the control node, Ansible can manage an entire fleet of machines and other devices (referred to as managed nodes) remotely with SSH, Powershell remoting, and numerous other transports, all from a simple command-line interface with no databases or daemons required.

To run the playbook, ensure that you have the latest version of Ansible installed. Please follow the steps below:

Update and Upgrade packages.

```bash
sudo apt update && sudo apt upgrade
```

Verify whether `pip` is already installed for your preferred [[Python Commands]].

```bash
python3 -m pip -V
```

If all is well, you should see something like the following:

```bash
pip 23.3.1 from /usr/lib/python3.12/site-packages/pip (python 3.12)
```

Use `pip` in your selected Python environment to install the Ansible package of your choice for the current user:

```bash
python3 -m pip install --user ansible
```

You can test that Ansible is installed correctly by checking the version:

```bash
ansible --version
```

If you see an error, See the Ansible documentation on [Installing Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) for more information.


##  Running the playbook

After pulling the playbook to your local environment, move into it's directory and change the values in host.yml and host_vars to point to the host you want to provision. 

To test connection execute the following command:


```bash
ansible all -m ping
```

you should get a message like this:


```bash
ubuntu-server-1 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
```

To run the playbook execute the following command:

```bash
ansible-playbook main.yml
```

Run the command with appropriate privileges,  administrative access is required to install and update packages.