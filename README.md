# Environment - Development

This repository contains a Docker Compose environment to spin-up some common service dependencies necessary for the local development of this application.

For the `static-file-server` container, you'll need to have some files to serve locally, especially to develop for [api-bio](https://github.com/starpep-web/api-bio), so make sure to check the [assets](https://github.com/starpep-web/assets) repo for more information on how to acquire those files.

## Requirements

In order to develop for this repository you need:

* [Docker](https://www.docker.com/products/docker-desktop/)

## Configuration

First, clone this repository:

```bash
git clone https://github.com/starpep-web/env-development
```

Create an `.env` file with the following contents:

```text
TIMEZONE=America/Guayaquil
NEO4J_TAG=latest
STATIC_FILES_LOCATION=/path/to/assets
```

> If you're using an ARM based computer (like an M-series Mac) set `NEO4J_TAG` to `latest-arm`.
> 
> As for `STATIC_FILES_LOCATION`, this variable should have the absolute path on your machine that points to the `files` folder of the project's [assets](https://github.com/starpep-web/assets). This is used by the `static-file-server` container to serve up these files which are required by some of the services in this application.

Start the environment:

```bash
docker compose up
```

And that's it, you will now have the following services running on your machine:

* A Redis cache available at `redis://localhost:6379`
* A Neo4j StarPep database instance available at `bolt://localhost:7687` and a web dashboard at `http://localhost:7474`
* A Nginx HTTP server with assets and exports served at `http://localhost:10000`

You may have to configure these addresses in some of the `.env` files in each of the different services.
