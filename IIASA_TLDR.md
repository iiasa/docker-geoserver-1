# docker-geoserver

## IIASA specific TLDR

 - Extensions will be downloaded when present in `build_data/stable_plugins.txt` during the build step. A full list of available can be found in `build_data/stable_plugins_available.txt`

 - Extensions can be enabled by editing `.env` (`STABLE_EXTENSIONS=plugin1,plugin2`)
   Downloaded extensions will be installed when creating the container (no need to rebuild the image, just `docker-compose up`).
   Extension .jars will always be exposed on the host system under `./geoserver_extensions`, *this is for debugging puposes* (usually you would not have to use this directory since there is automated extension installation).

 - The data directory location inside the container can be adjusted with `GEOSERVER_DATA_DIR`.
   It will always be exposed on the host system under `./geoserver_data` (for data imports).

  - *both of these directories must exist!!*

 - Tomcat will be routed to Port `:8600` by docker.

 - To adjust admin credentials, once again edit the `.env` file (`GEOSERVER_ADMIN_USER` and `GEOSERVER_ADMIN_PASSWORD`).
   *it his highly advisable to do this before building the docker image and running it for the first time* since some data in the persistent data directory might be encrypted with this password and changing it will require manual intervention.

 - The docker project name is defined with the property `COMPOSE_PROJECT_NAME` *it should be different from the previous name* as the old docker volumes might persist which breaks things.

 - Updating this repo (merging back into the fork) and rebuilding the docker image should be *reoccuring tasks*.
