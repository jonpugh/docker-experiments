# Docker Experiments

This repo is full of experiments with docker.


# Experiment #1

**Goal:** Get docker-compose to be able to launch a drupal site.

Dug through the docker-compose documentation, the old fig documentation, still trying to wrap my head around all of the moving parts and how the "official" images work.

The "official" mysql images will not work with this docker-compose.yml file, and I didn't find out why yet.

The other problem with official mysql and mariadb images is they have a documented limitation with docker-compose:

See https://registry.hub.docker.com/_/mariadb/ and https://registry.hub.docker.com/_/mysql

> If there is no database initialized when the container starts, then a default database will be created. While this is the expected behavior, this means that it will not accept incoming connections until such initialization completes. This may cause issues when using automation tools, such as docker-compose, which start several containers simultaneously.