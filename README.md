# Docker Experiments

This repo is full of experiments with docker.


# Experiment #1

**Goal:** Get docker-compose to be able to launch a drupal site.

Dug through the docker-compose documentation, the old fig documentation, still trying to wrap my head around all of the moving parts and how the "official" images work.

The "official" mysql images will not work with this docker-compose.yml file, and I didn't find out why yet.

The other problem with official mysql and mariadb images is they have a documented limitation with docker-compose:

See https://registry.hub.docker.com/_/mariadb/ and https://registry.hub.docker.com/_/mysql

> If there is no database initialized when the container starts, then a default database will be created. While this is the expected behavior, this means that it will not accept incoming connections until such initialization completes. This may cause issues when using automation tools, such as docker-compose, which start several containers simultaneously.

## Steps 

1. clone this repo.
2. Download drupal, prepare for install.
  ```
  drush dl drupal  These will be automatically overridden by the system 

  mv drupal-7.xx src
  mkdir src/sites/default/files
  sudo chown www-data src/sites/default/files
  cp src/sites/default/default.settings.php src/sites/default/settings.php
  sudo chown www-data src/sites/default/settings.php
  ```
2. docker-compose up
3. Load http://localhost:8000/
4. You should be redirected to http://localhost:8000/install.php and the drupal install page.
5. Go through the profile selection process, you will end up on the database credentials page.  
  The database name, username, and password are all `drupal`.  They were set in docker-compose.yml.
  
  The host should be set to `db`. *This is so it matches the "link" to the docker container named "db"*
  
  Hopefully, the database connected and your drupal site installs!
  
  
  