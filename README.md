# Install RancherOS, Traefik, Let's Encrypt & Rancher Server
Boot Rancher OS from the iso image, then follow the instructions.

## 1. Clone this repository
```
git clone https://github.com/matjazmav/rancheros-config.git
```

## 2. Install RancherOS
Check the config file: cloud-config.yml (ssh keys, interface, ...)

```bash
sudo ros install -c cloud-config.yml -d /dev/sda
```
After that restart computer. Now you should SSH to your machine.

## 3. Start the services
Check the config files:

    - configs/traefik/traefik.toml (email, domain, ...)
    - docker-compose.yml (domain, ...)

```bash
# Create network for Traefik porxy
docker network create web

# Start docker-compose
docker-compose up -d
```

## 2. Configure Rancher server
### 1. Admin user
Go to *Admin -> Access Controll -> Local* and create Admin user.
### 2. Add hosts
Go to *Infrastructure -> Hosts -> Add Host*, click *Save* and copy the docker command to the host machine.
