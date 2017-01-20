#PressBoxx

## Setup
1. Clone this repository
1. Execute `docker-compose up`
1. Open [http://localhost](http://localhost) in your browser.
1. Edit the `docker-compose.yml` file to mount your working directory.
On Mac OSX, this is usually the `Sites` subdirectory of the user home
directory. You will need to change lines 27 and 44, where the volumes
are defined for the `php7-fpm` and `web` containers. For example, change
`~/working:/usr/share/nginx` to `~/Sites:/usr/share/nginx`.
1. You will also need to edit the `site.conf` file in the `docker/projects`
directory of this repository. On line 4 of the aforementioned file,
you will need to point this to the web root of the project you wish to
have Nginx serve.

## How does Xdebug work?

Xdebug is availaible in the PHP-FPM Container. In order to use it with
PHPStorm, you will need to create an alias ethernet adapter. This can
be done on Mac OSX using the following command:

`sudo ifconfig en0 alias 10.254.254.254 255.255.255.0`

In addition, the DBG Proxy must also be configured to listen to the\
same IP address on port `9000`.

Detailed instructions can be found [here](http://jamescowie.me/blog/2016/12/all-hail-xdebug-and-lets-let-var-dump-die/).