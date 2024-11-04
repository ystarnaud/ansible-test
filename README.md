# Set up end-user development environments with Ansible

Installs required packages for development environments:

* Homebrew
* docker
* docker-compose
* docker-machine
* git
* jq
* openssl
* pyenv
* python 2.7.18
* pip 20.3.4
* ssh-copy-id
* wget
* zsh
* zsh-syntax-highlighting


## Requirements

Base System: Debian 12.7

Required Packages:
* curl
* git
* build-essential
* ansible

Pre-configuration on Debian:
```
UBUNTU_CODENAME=jammy​
wget -O- "https://keyserver.ubuntu.com/pks/lookup?fingerprint=on&op=get&search=0x6125E2A8C77F2818FB7BD15B93C4A3FD7BB9C367" | sudo gpg --dearmour -o /usr/share/keyrings/ansible-archive-keyring.gpg​
echo "deb [signed-by=/usr/share/keyrings/ansible-archive-keyring.gpg] http://ppa.launchpad.net/ansible/ansible/ubuntu $UBUNTU_CODENAME main" | sudo tee /etc/apt/sources.list.d/ansible.list​
sudo apt update && sudo apt install ansible git curl build-essential​
```

## Usage

Running the Ansible Playbook:
```
wget https://raw.githubusercontent.com/ystarnaud/ansible-test/HEAD/dev_playbook.yml​
ansible-playbook dev_playbook.yml​
```

## Notes
During the installation, the script may stop when needing the shell environment restarted. When this occurs, restart the shell or simply run `source ~/.bashrc`, then resume the playbook with `ansible-playbook dev_playbook.yml`. Below is an example:

```
TASK [Set Homebrew Environment] ******************************************************************************************************************************
ok: [localhost]

TASK [Restart shell or run the following command: source ~/.bashrc before continuing.] ***********************************************************************

PLAY RECAP ***************************************************************************************************************************************************
localhost                  : ok=5    changed=1    unreachable=0    failed=0    skipped=1    rescued=0    ignored=2

user@ansible-test:~$ source ~/.bashrc
user@ansible-test:~$ ansible-playbook test.yaml
```



