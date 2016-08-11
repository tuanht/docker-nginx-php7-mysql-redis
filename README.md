# Summary
Docker Compose to start development environment for PHP web app using Symfony

# Development stack
- Nginx 1.10.1
- PHP7-FPM with following extensions: Xdebug 2.4.0, PhpRedis 3.0.0, PDO MySQL, ACPU & Opcache
- MySQL 5.7.13
- Redis 3.0.7

# ~~Vagrant~~
~~For OSX & Windows users who don't want to install Docker on real machine, I builded a `Vagrantfile` so you can up and ssh to virtual machine. Remember mount your project folder into virtual machine, so docker can continue to mount into container.~~ :warning: Deprecated: Please use `docker-machine` instead.

# Speedup Docker
:warning: Mac OS X only

[Docker Machine NFS](https://github.com/adlogix/docker-machine-nfs) help activate NFS for an existing boot2docker box created through Docker Machine.
```sh
$ brew install docker-machine-nfs
$ docker-machine-nfs default --mount-opts="nolock,vers=3,udp,noatime"
```
