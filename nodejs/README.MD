## Node.js Quickstart 

This is the source for the Node.js Quickstart Droplet image. 

## Features

- Node v12.16.0 (Stable)
- `pm2` used for process management and scheduling Node/your app to start at boot time
- Nginx installed w/reverse proxy pre-configured
- Built-in Node.js app that self-documents how to put your code on the Droplet and run it via the reverse proxy
- UFW firewall pre-configured 

## To Recreate This Image

1. Start a new Ubuntu Droplet
2. Install Node.js following these instructions: https://github.com/nodesource/distributions/blob/master/README.md#debinstall
3. Install pm2: `sudo npm install pm2@latest -g --no-optional`
4. `git clone` this repo
5. `cd ~/oneclick-quickstarts/nodejs/var`
6. `mv www /var`
7. `cd /var/www/html`
8. `pm2 start hello.js`
9. `pm2 startup systemd`
10. `pm2 save`
11. `sudo apt update`
12. `sudo apt install nginx`
13. `sudo ufw allow 'Nginx Full'`
14. `cd ~/oneclick-quickstarts/nodejs/etc/nginx/sites-available`
15. `mv default /etc/nginx/sites-available/`
16. `sudo systemctl restart nginx`
