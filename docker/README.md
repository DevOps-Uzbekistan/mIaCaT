# Ansible Playbook for Docker Installation

This Ansible playbook is designed to automate the installation of Docker on Ubuntu and RHEL based systems.

## Features

- Installs required system packages
- Adds Docker's repository to package manager
- Installs Docker Engine, Docker CLI, containerd.io, Docker Buildx Plugin, and Docker Compose Plugin
- If a specific version is defined in the `version_string` variable, it installs that version. Otherwise, it installs the latest version.
  - To check the list of available versions on Ubuntu: `apt-cache madison docker-ce | awk '{ print $3 }'`
  - To check the list of available versions on RHEL:  `yum list docker-ce --showduplicates | sort -r`

## Requirements

To use this Ansible playbook for Docker installation, you will need:

1. A remote user with sudo privileges
2. An inventory file to run the Ansible playbook on

## Usage

1. Clone this repository to your local machine.
2. Navigate to the directory containing the playbook.
3. Run the playbook using the following command:

```bash
ansible-playbook ../docker.install.yml --extra-vars "host=my_host user=my_user"  #Don't forget to change the actual value and -K required for sudo password 
```

## Variables

| Variables         | Default                                                                                   |  Description
|-------------------|-------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------
| deb_architecture  | { `"x86_64": "amd64"`, `"aarch64": "arm64`"}                                              | A dictionary mapping system architectures to Docker architectures
| version_string    | `null`                                                                                    | Define this variable if you want to install a specific version of Docker. If not defined or left as an empty string, the playbook will install the latest version.


> **_NOTE:_**  The note content.


License
-------

[MIT](https://github.com/DevOps-Uzbekistan/mIaCaT/blob/main/LICENSE)

Author Information
------------------

Group: DevOps Uzbekistan

Telegram: https://t.me/devopsuzb

