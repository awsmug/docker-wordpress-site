# Docker WordPress Site 
*Nginx, PHP (Xdebug), MariaDB and WordPress*

This is a docker template for WordPress developments for working on whole site projects.

This webserver contains a basic configuration with

* nginx (latest)
* php (7-fpm) - configured with xdebug
* mariadb (latest)
* WordPress (latest)

## Configure your environment

### General setup for your WordPress project

Copy the files from this repository to an empty directory where you would like to develop your WordPress project and
run `docker-compose up`. After that WordPress will be installed and WordPress root directory will be mapped to 
`src` folder in the directory where you can leave your project files.

Your will reach your server under `http://localhost/` with a ready installed WordPress.

## Reinstall WordPress

ATTENTION! 

The reinstallation of WordPress will be a vanilla installation. All data from the wp-content directory will
replaced by the content of a fresh WordPress installation. Take care to backup your development data from this directory
before!

To start the reinstallation insert the variable `WP_INSTALL: fresh` in the `environment` section of WP in the 
docker-compose.yml file and start the server by `docker-compose up` command.

### PHP Settings

The default xdebug port is set to 9001. Make sure that you change the IP address to your local IP address you will get 
with the `ifconfig` command on your console. You have to change it in the file  `conf/php/php.ini`.

`xdebug.remote_host={YOUR-IP-ADDRESS}`

Also you can setup further xdebug or php settings in the php.ini file.

### PhpStorm Settings

Enter the remote host port in `PhpStorm > Preferences` under the nodes Languages and `Frameworks > PHP > Debug` in 
the field `XDebug > Debug Port` to the port you have entered at your php.ini.

### Webserver settings

The nginx host by default is `localhost`. You can change the host it in the  `conf/nginx/nginx.conf`. But please 
keep in mind to add the host entry to your local `/etc/hosts` file with en entry like this:

`127.0.0.1 your-host-name`

## Launching Webserver

Start the webserver with the command `docker-compose up` and stop it with `docker-compose down`.

