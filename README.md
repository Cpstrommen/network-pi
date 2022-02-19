# network-pi: A bouncer for your local network
A collection of docker containers to provide enterprise-level services for a home network all hosted from a Raspberry Pi

Thank you to Jeff Geerling for inspiration and a framework for this project in his [internet-pi project](https://github.com/geerlingguy/internet-pi)
## Installation
### Requirements
* Docker    `sudo apt-get install docker`
    * Add user to the docker group with `sudo usermod -aG docker <username>`
* Docker Compose    `sudo apt-get install docker-compose`
* Ansible   `pip3 install ansible`
    * Python can be installed with `sudo apt install python3` 
    * Pip3 can be installed with `sudo apt install python3-pip`
* Optional: Portainer or Rancher for container management

### Configuration
- Edit `config.yml` to meet your requirements
- Change details in `docker-compose.yml` for your network

### Installation
- Clone this repository and `cd network-pi`
- Install Ansible requirements with `ansible-galaxy collection install -r requirements.yml`
- Run the base Ansible playbook to install the framework `ansible-playbook main.yml`
- Create the docker containers with `docker-compose up -d`

## Contribution Notes
Since this is a pi-based project, please confirm all included docker images are compatible with arm64 systems