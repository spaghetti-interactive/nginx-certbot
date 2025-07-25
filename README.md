# Boilerplate for nginx with Let’s Encrypt on docker-compose

> This repository is accompanied by a [step-by-step guide on how to
set up nginx and Let’s Encrypt with Docker](https://medium.com/@pentacent/nginx-and-lets-encrypt-with-docker-in-less-than-5-minutes-b4b8a60d3a71).

`init-letsencrypt.sh` fetches and ensures the renewal of a Let’s
Encrypt certificate for one or multiple domains in a docker-compose
setup with nginx.
This is useful when you need to set up nginx as a reverse proxy for an
application.

## Installation
1. [Install docker-compose](https://docs.docker.com/compose/install/#install-compose).

2. Clone this repository: `git clone https://github.com/wmnnd/nginx-certbot.git .`

3. Modify configuration:
- Add domains and email addresses to init-letsencrypt.sh
- Replace all occurrences of example.org with primary domain (the first one you added to init-letsencrypt.sh) in data/nginx/app.conf

4. Run the init script:

        ./init-letsencrypt.sh

5. Run the server:

        docker-compose up

## Got questions?
Feel free to post questions in the comment section of the [accompanying guide](https://medium.com/@pentacent/nginx-and-lets-encrypt-with-docker-in-less-than-5-minutes-b4b8a60d3a71)

## License
All code in this repository is licensed under the terms of the `MIT License`. For further information please refer to the `LICENSE` file.



#Giochipiu

Add new website:
- Create .conf file under data/nginx (es: mkdir ./data/nginx && cp -R ./data/nginx_srv_dockprom/* ./data/nginx)
<!-- - edit init-letsencrypt.sh with new domain -->
- make sure you've added only the new domain website config and all nginx configurations is well formed before launching next command
- execute sudo ./init-letsencrypt.sh domain.ext

if needed execute to restart docker
- docker-compose down && docker-compose up -d

rotate logs: https://alexanderzeitler.com/articles/rotating-nginx-logs-with-docker-compose/

copy logrotate script: cp ./logrotate /etc/logrotate.d/nginx

test logrotate: logrotate -f /etc/logrotate.d/nginx
