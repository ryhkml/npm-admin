## ALLOW IN or DENY IN - [Nginx Proxy Manager](https://nginxproxymanager.com) Admin Panel

### First of all

You need to fix the Docker and UFW security flaw without disabling iptables. Follow this steps and backup your ufw `after.rules` config

```bash
sudo cp /etc/ufw/after.rules /etc/ufw/after.rules-COPY
```
```bash
sudo curl -s -o /usr/local/bin/ufw-docker https://raw.githubusercontent.com/chaifeng/ufw-docker/master/ufw-docker && \
  sudo chmod +x /usr/local/bin/ufw-docker && \
  sudo ufw-docker install && \
  sudo systemctl restart ufw
```

More information, visit: https://github.com/chaifeng/ufw-docker

### Usage

#### Allow NPM admin panel

Attention, if http and https are listed in the UFW state, delete them. UFW http and https are no longer needed

```bash
sudo ufw allow delete http && \
  sudo ufw allow delete https
```
then

```bash
sudo curl -o /usr/local/bin/npm-admin https://raw.githubusercontent.com/ryhkml/npm-admin/main/npm-admin && \
  sudo chmod +x /usr/local/bin/npm-admin && \
  sudo npm-admin init && \
  sudo npm-admin allow
```
or you can specific allow from your subnet/cidr or any
```bash
sudo npm-admin allow <SUBNET_CIDR|any>
```
Default is your public IP. `any` or `0.0.0.0/0` means, the NPM admin panel can be access from anywhere

#### Delete rule NPM admin panel
```bash
sudo npm-admin delete
```

### How to update

```bash
sudo rm -f /usr/local/bin/npm-admin && \
  sudo curl -s -o /usr/local/bin/npm-admin https://raw.githubusercontent.com/ryhkml/npm-admin/main/npm-admin && \
  sudo chmod +x /usr/local/bin/npm-admin
```