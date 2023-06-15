## ALLOW IN or DENY IN - Admin Panel [Nginx Proxy Manager](https://nginxproxymanager.com)

First of all, backup your ufw `after.rules` config

```bash
sudo cp /etc/ufw/after.rules /etc/ufw/after.default.rules
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

More info, visit: https://github.com/chaifeng/ufw-docker

### Usage

#### Show admin panel

```bash
sudo curl -o /usr/local/bin/npm-admin https://raw.githubusercontent.com/ryhkml/npm-admin/main/npm-admin
```
```bash
sudo chmod +x /usr/local/bin/npm-admin
```
How to get a Docker container IP address from the host?

```bash
docker inspect [CONTAINER_NGINX_PROXY_MANAGER_ID] | grep "IPAddress"
```
then

```bash
sudo npm-admin show [YOUR_IP_ADDRESS or YOUR_IP_RANGE or any] [CONTAINER_NGINX_PROXY_MANAGER_IP_ADDRESS]
```
any or 0.0.0.0/0 means, the admin panel can be accessed from anywhere

#### Delete rules admin panel
```bash
sudo npm-admin delete
```