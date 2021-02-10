# docker-geoserver

## IIASA specific TLDR

 - copy `.env.tpl` to `.env` and fill in the proper admin password and port (8223=testing, 8222=production) (`GEOSERVER_ADMIN_PASSWORD`, `HOST_SYSTEM_PORT`)

 - Extensions will be downloaded when present in `build_data/stable_plugins.txt` during the build step. A full list of available can be found in `build_data/stable_plugins_available.txt`

 - Extensions can be enabled by editing `.env` (`STABLE_EXTENSIONS=plugin1,plugin2`)
   Downloaded extensions will be installed when creating the container (no need to rebuild the image, just `docker-compose up`).

 - The data directory location inside the container can be adjusted with `GEOSERVER_DATA_DIR`.
   It will always be exposed on the host system under `./geoserver_data` (for data imports).

 - Tomcat will be routed to Port `:8600` by docker.

 - To adjust admin credentials, once again edit the `.env` file (`GEOSERVER_ADMIN_USER` and `GEOSERVER_ADMIN_PASSWORD`).
   *it his highly advisable to do this before building the docker image and running it for the first time* since some data in the persistent data directory might be encrypted with this password and changing it will require manual intervention.

 - The docker project name is defined with the property `COMPOSE_PROJECT_NAME`

 - Updating this repo (merging back into the fork) and rebuilding the docker image should be *reoccuring tasks*.
