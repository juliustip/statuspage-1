# Cachet Statuspage
Distribution of of [Cachet] aiming to provide a fully automated monitoring Docker stack utilising
their official [Cachet-Docker] image, [Cachet-Monitor] and a custom service(TODO) for more advanced metrics.

### Requirements
- Docker Engine ([install script](https://docs.docker.com/engine/installation/linux/docker-ce/centos/#install-using-the-convenience-script))
- Docker Compose ([install](https://docs.docker.com/compose/install/))

## Introduction
Telling [docker-compose] to start the stack will spin up 3 containers.
- A PostgreSQL container that acts as a database for Cachet using the files in [sql/](./sql/) to initialise the DB with basic data
- A Cachet container that is the main web service that serves the status page
- A Cachet-Monitor container that handles the automated monitoring and incident opening of each component.

## Getting Started
1. Clone this repo
```shell
git clone https://github.com/juliustip/Cachet-Automated-Monitor.git
```

2. Optionally update the [`docker-compose.yml`](./docker-compose.yml) ENV vars. You should probably specify your own APP_KEY, which is detailed in [Cachet's README]

3. Build the `cachet-monitor` image
```shell
docker build -t cachet-monitor:0.1 cachet-monitor/
```

4. Run the stack
```shell
docker-compose up
```

[Cachet]: https://cachethq.io/
[Cachet-Docker]: https://github.com/CachetHQ/Docker
[Cachet's README]: https://github.com/CachetHQ/Docker#quickstart
[Cachet-Monitor]: https://github.com/CastawayLabs/cachet-monitor
[docker-compose]: https://docs.docker.com/compose/
