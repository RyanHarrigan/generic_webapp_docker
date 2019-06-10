# Generic Webapp Docker Setup

This docker config is meant primarily for local development prototyping. **NOT MEANT FOR PRODUCTION.** The mysql config exposes its port to the host so that you can run scripts like `wordmove` or even manually load/dump/debug. I primarily use this config repo for WordPress, but can be used for any PHP-based web app.

nginx's default.conf doesn't read from environment variables, so I set the local URL to `wordpress.local`

## Dependencies

Install the following dependencies through their respective installation instructions:
* `docker`
* `docker-machine`
* `docker-compose`
* `wordmove`
* `wp-cli`

## Dotenv

Included is a .env_sample file. Since Docker and Wordmove utilize dotenv, it's convenient to define all environment variables there. 

## Web App Setup

### Initialize Docker
1. Make sure your Docker machine is running: `docker-machine start`
2. After you have an IP provisioned (usually 192.168.99.100), load the docker machine environment variables ```eval `docker-machine env` ```
3. Then fire up your docker images `docker-compose up -d` (I have issues with Linux and need `sudo` to provision volumes/ports)


### Initialize Your Web Files
The webroot folder can hold any PHP files you want. The following command installs WordPress without default plugins/themes:
`wp core download --path=webroot --skip-content`

Edit your Windows/Mac/Linux 'hosts' file to point the url `worpdress.local` to the IP address provisioned by your docker machine.

### Have Fun
Star this repo if you want.