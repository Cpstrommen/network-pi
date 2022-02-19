# network-pi: A bouncer for your local network
A collection of docker containers to provide enterprise-level services for a home network all hosted from a Raspberry Pi

Thank you to Jeff Geerling for inspiration and a framework for this project in his [internet-pi project](https://github.com/geerlingguy/internet-pi)

## Features

### Ansible-installed Features
* Grafana 
* Prometheus
* Power monitoring using shelly WiFi plug
* Network monitoring using Speedtest
### Docker Features
* PiHole - Local DNS server for adblocking and internet privacy
* Homer - Dashboard for locally hosted services
* Homebridge - Third-party device support for Apple Homekit
* Wireguard - VPN server for local network access

## Installation
### Requirements
* Raspberry Pi running RaspberryPiOS or your distro of choice
    * Pi 4 4gb or better recommended if you intend to implement the full feature set
* Docker    `sudo apt-get install docker`
    * Add user to the docker group with `sudo usermod -aG docker <username>`
* Docker Compose    `sudo apt-get install docker-compose`
* Ansible   `pip3 install ansible`
    * Python can be installed with `sudo apt install python3` 
    * Pip3 can be installed with `sudo apt install python3-pip`
* Optional: Portainer or Rancher for container management

### Configuration
- Edit `example-config.yml` to meet your requirements and copy to `config.yml`
- Change details in `example-docker-compose.yml` for your network and copy to `docker-compose.yml`
- Add details to `example-inventory.ini` and copy to `inventory.ini`

### Installation
- Clone this repository and `cd network-pi`
- Install Ansible requirements with `ansible-galaxy collection install -r requirements.yml`
- Run the base Ansible playbook to install the framework `ansible-playbook main.yml`
- Create the docker containers with `docker-compose up -d`
    * For Portainer and Rancher, create and deploy a new stack using the contents of `docker-compose.yml`

### Post-installation Configuration
- Add DNS blocklists to PiHole avaliable at [The Firebog](https://v.firebog.net/hosts/lists.php)
    * Optional: add local DNS names for each local service's web UI in the PiHole UI
- Customize Homer dashboard by editing `/homer/config.yml` on the host
- Add HomeBridge to Apple Homekit by using the web gui at `server-ip:8581`
- Fetch VPN peer keys from `./config/wireguard` on the host

### Web UI Locations
- PiHole at `server-ip:81`
- Homer at `server-ip:80`
- Homebridge at `server-ip:8581`
- Grafana at `server-ip:3030`

## Contribution Notes
Since this is a pi-based project, please confirm all included docker images are compatible with arm64 systems