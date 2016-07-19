# Docker Codeception Example
This is an example of [Codeception](http://codeception.com/) on docker containers.

## Install
### VirtualBox
Download installer and install.<br>
https://www.virtualbox.org/wiki/Downloads

### Docker toolbox
Download installer and install.<br>
https://www.docker.com/products/docker-docker-compose

The following components are installed.
- Docker Engine
- Compose
- Machine
- Kitematic

## Setup
### Starting docker-machine
```
$ docker-machine start default
```

### Setting environment variables
```
$ docker-machine env default
export DOCKER_TLS_VERIFY="1"
export DOCKER_HOST="tcp://192.168.99.100:2376"
export DOCKER_CERT_PATH="/path/to/home/.docker/machine/machines/default"
export DOCKER_MACHINE_NAME="default"
# Run this command to configure your shell:
# eval $(docker-machine env default)
```

```
$ eval $(docker-machine env default)
```

### Starting Docker compose
```
$ docker-compose up -d --build
```

### Run php container and composer install

```
$ docker-compose run php bash
```

```bash
root@{container id}:/var/www/symfony.demo# bin/composer self-update
root@{container id}:/var/www/symfony.demo# bin/composer install
```

### Run acceptance tests
```bash
root@{container id}:/var/www/symfony.demo# bin/codecept run
Codeception PHP Testing Framework v2.2.2
Powered by PHPUnit 5.4.6 by Sebastian Bergmann and contributors.

Acceptance Tests (2) -------------------------------------------------------------------------------------------------------------------------------
Testing acceptance
✔ BlogCept: Open blog page and see article there (6.664s)
✔ LoginCept: Login as admin to backend (10.1009s)
----------------------------------------------------------------------------------------------------------------------------------------------------


Time: 18.48 seconds, Memory: 13.25MB

OK (2 tests, 5 assertions)
```

### Run acceptance tests with VNC client
- For Mac
  - Starting `Finder`.
  - Use `Connect to Server`.
  - Input `vnc://${docker-machine ip default}:5900` to `Server Address`.
  - Input `secret` to `Password`.

- Run acceptance tests
  - Execute `bin/codecept run` command in php container.

