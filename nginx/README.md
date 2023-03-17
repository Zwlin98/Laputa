# Nginx Gateway

## Install Nginx Using nginx packages repository

[Installation Guide](https://nginx.org/en/linux_packages.html#Debian) for other distributions.

Debian as follows:
```bash

sudo apt install curl gnupg2 ca-certificates lsb-release debian-archive-keyring

curl https://nginx.org/keys/nginx_signing.key | gpg --dearmor \
    | sudo tee /usr/share/keyrings/nginx-archive-keyring.gpg >/dev/null

echo "deb [signed-by=/usr/share/keyrings/nginx-archive-keyring.gpg] \
http://nginx.org/packages/debian `lsb_release -cs` nginx" \
    | sudo tee /etc/apt/sources.list.d/nginx.list

echo -e "Package: *\nPin: origin nginx.org\nPin: release o=nginx\nPin-Priority: 900\n" \
    | sudo tee /etc/apt/preferences.d/99nginx

sudo apt update
sudo apt install nginx
```

## Modify Nginx Configuration in conf.d

For example: 
```bash
cp conf.d/template.conf /etc/nginx/conf.d/synapse.conf

# then configure the port and ws_path in synapse.conf
```

## SSL with Let's Encrypt


```bash
apt install certbot python3-certbot-nginx

certbot --nginx
```