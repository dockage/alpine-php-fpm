# alpine-php-fpm [![Docker Pulls](https://img.shields.io/docker/pulls/dockage/alpine-php-fpm.svg)](https://hub.docker.com/r/dockage/alpine-php-fpm/) [![Docker Stars](https://img.shields.io/docker/stars/dockage/alpine-php-fpm.svg?style=flat)](https://hub.docker.com/r/dockage/alpine-php-fpm/) [![MicroBadger](https://images.microbadger.com/badges/image/dockage/alpine-php-fpm:3.6.svg)](https://microbadger.com/images/dockage/alpine-php-fpm:3.6) [![Docker Build Status](https://img.shields.io/docker/build/dockage/alpine-php-fpm.svg)](https://hub.docker.com/r/dockage/alpine-php-fpm/) [![Docker Automated build](https://img.shields.io/docker/automated/dockage/alpine-php-fpm.svg)](https://hub.docker.com/r/dockage/alpine-php-fpm/)
FPM (FastCGI Process Manager) is an alternative PHP FastCGI implementation with some additional features (mostly) useful for heavy-loaded sites.

## Contributing

If you find this image useful here's how you can help:

- Send a pull request with your awesome features and bug fixes
- Help users resolve their [issues](../../issues?q=is%3Aopen+is%3Aissue).

## Issues

Before reporting your issue please try updating Docker to the latest version and check if it resolves the issue. Refer to the Docker [installation guide](https://docs.docker.com/installation) for instructions.

SELinux users should try disabling SELinux using the command `setenforce 0` to see if it resolves the issue.

If the above recommendations do not help then [report your issue](../../issues/new) along with the following information:

- Output of the `docker vers6` and `docker info` commands
- The `docker run` command or `docker-compose.yml` used to start the image. Mask out the sensitive bits.
- Please state if you are using [Boot2Docker](http://www.boot2docker.io), [VirtualBox](https://www.virtualbox.org), etc.

# Getting started

## Installation

Automated builds of the image are available on [Dockerhub](https://hub.docker.com/r/dockage/alpine-php-fpm) and is the recommended method of installation.

> **Note**: Builds are also available on [Quay.io](https://quay.io/repository/dockage/alpine-php-fpm)

```bash
docker pull dockage/alpine-php-fpm:3.6
```

Alternatively you can build the image yourself.

```bash
docker build -t dockage/alpine-php-fpm github.com/dockage/alpine-php-fpm
```

### Available Configuration Parameters

*Please refer the docker run command options for the `--env-file` flag where you can specify all required environment variables in a single file. This will save you from writing a potentially long docker run command. Alternatively you can use docker-compose.*

Below is the complete list of available options that can be used to customize your `php-fpm` installation. All these environments and keys use in [`confd`](http://confd.io)

| Environment | Key | Description |
|-----|-----------|-------------|
| `PHP_FPM_USER` | `/php-fpm/user` | Unix user of processes. Defaults to `nobody`. |
| `PHP_FPM_GROUP` | `/php-fpm/group` | Unix group of processes. Defaults to `nobody`. |
| `PHP_FPM_LISTEN` | `/php-fpm/listen` | The address on which to accept FastCGI requests. Defaults to `127.0.0.1:9000`. |
| `PHP_FPM_LISTEN_OWNER` | `/php-fpm/listen/owner` | Set permissions for unix socket, if one is used. Defaults to `nobody`. |
| `PHP_FPM_LISTEN_GROUP` | `/php-fpm/listen/group` | Set permissions for unix socket, if one is used. Defaults to `nobody`. |
| `PHP_FPM_LISTEN_MODE` | `/php-fpm/listen/mode` | Set permissions for unix socket, if one is used. Defaults to `0660`. |
| `PHP_FPM_PM` | `/php-fpm/pm` | Choose how the process manager will control the number of child processes, Possible Values: `static`, `dynamic` or `ondemand`. Defaults to `dynamic` |
| `PHP_FPM_PM_MAX_CHILDREN` | `/php-fpm/pm/max_children` | The number of child processes to be created when pm is set to 'static' and the maximum number of child processes when pm is set to 'dynamic' or 'ondemand'. This value sets the limit on the number of simultaneous requests that will be served. Defaults to `5`. |
| `PHP_FPM_PM_START_SERVERS` | `/php-fpm/pm/start_servers` | The number of child processes created on startup. Note: Used only when pm is set to `dynamic`, Default Value: `min_spare_servers + (max_spare_servers - min_spare_servers) / 2` Defaults to `2`. |
| `PHP_FPM_PM_MIN_SPARE_SERVERS` | `/php-fpm/pm/min_spare_servers` | The desired minimum number of idle server processes. **Note:** Used only when pm is set to `dynamic`. **Note:** Mandatory when pm is set to `dynamic`. Defaults to `1`. |
| `PHP_FPM_PM_MAX_SPARE_SERVERS` | `/php-fpm/pm/max_spare_servers` | The desired maximum number of idle server processes. **Note:** Used only when pm is set to `dynamic`. **Note:** Mandatory when pm is set to `dynamic`. Defaults to `3`. |
| `PHP_FPM_PM_MAX_REQUESTS` | `/php-fpm/pm/max_requests` | The number of requests each child process should execute before respawning. Defaults to `0`. |
