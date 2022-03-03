# data.gtdb.ecogenomic.org

This repository contains the infrastructure required to
serve [data.gtdb.ecogenomic.org](https://data.gtdb.ecogenomic.org/).

## Contributing

This project uses [Semantic Versioning](http://semver.org/) and [Conventional Commits](https://conventionalcommits.org/)
to automatically generate release notes using [Semantic Release](https://semantic-release.gitbook.io/semantic-release/).

Please ensure that your commits are property formatted.

## Setup

If you are installing this on a fresh VM, then you will need to follow these setup guides:

* [VM Setup](doc/vm_setup.md)
* [Docker setup](doc/docker.md)

## Controlling services

The following commands will be available to you when in the current directory:

* Start: `docker-compose up -d`
* Stop: `docker-compose down`
