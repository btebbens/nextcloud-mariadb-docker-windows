# nextcloud-mariadb-docker-windows

1) Edit users/passwords in `/app-nextcloud/docker-compose.yml` as desired
   * Note: `MARIADB_USER` and `MARIADB_PASSWORD` must match `MYSQL_USER` and `MYSQL_PASSWORD`, respectively 
2) `cd` to `/app-nextcloud` 
3) Run 'docker compose up'
4) Wait for the message `nextcloud  | Nextcloud was successfully installed`
5) Press `ctrl+c` to stop the containers
6) Edit `/app-nextcloud/docker-compose.yml` and remove both `environment` sections
7) Run 'docker compose up -d'
8) Navigate to http://localhost:8080
9) Log in with the admin user specified and verify everything is working