## ALLOW IN or DENY IN - [Nginx Proxy Manager](https://nginxproxymanager.com) Admin Panel

### First of all

You need to fix the Docker and UFW security flaw without disabling iptables. Follow this steps and backup your ufw `after.rules` config

```bash
sudo cp /etc/ufw/after.rules /etc/ufw/after.rules-COPY
```
```bash
sudo curl -o /usr/local/bin/ufw-docker https://raw.githubusercontent.com/chaifeng/ufw-docker/master/ufw-docker
```
```bash
sudo chmod +x /usr/local/bin/ufw-docker
```
```bash
sudo ufw-docker install
```
```bash
sudo systemctl restart ufw
```

More information, visit: https://github.com/chaifeng/ufw-docker

### Usage

#### Show NPM admin panel

Attention, if http and https are listed in the UFW state, delete them. UFW http and https are no longer needed

```bash
sudo ufw allow delete http && sudo ufw allow delete https
```
then

```bash
sudo curl -o /usr/local/bin/npm-admin https://raw.githubusercontent.com/ryhkml/npm-admin/main/npm-admin
```
```bash
sudo chmod +x /usr/local/bin/npm-admin
```
```bash
sudo npm-admin init <CONTAINER_NPM_NAME|CONTAINER_NPM_ID>
```
```bash
sudo npm-admin show <CONTAINER_NPM_NAME|CONTAINER_NPM_ID> <YOUR_PUBLIC_IP|CIDR|any>
```
`any` or `0.0.0.0/0` means, the NPM admin panel can be access from anywhere

#### Delete rules NPM admin panel
```bash
sudo npm-admin delete
```