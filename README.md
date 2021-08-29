# nextcloud-mariadb-docker-windows

This guide assumes you are using Docker Desktop 19.03.0+ with the Hyper-V backend

## Setup

1) Edit users/passwords in `/app-nextcloud/docker-compose.yml` as desired
   * Note: `MARIADB_USER` and `MARIADB_PASSWORD` must match `MYSQL_USER` and `MYSQL_PASSWORD`, respectively 
2) `cd` to `/app-nextcloud` 
3) Run 'docker compose up'
4) Wait for the message `nextcloud  | Nextcloud was successfully installed`
5) Press `ctrl+c` to stop the containers
6) Edit `/app-nextcloud/docker-compose.yml` and remove both `environment:` sections
7) Run 'docker compose up -d'
8) Navigate to http://localhost:8080
9) Log in with the admin user specified and verify everything is working

## Using shared paths

1) Remove `database:` and/or `data:` under the root `volumes:` in `docker-compose.yml`
2) Change the `database:` and/or `data:` under `volumes:` of the corresponding service in to the desired path (e.g. `C:\NextCloud:/var/www/html`)
3) Answer `Share It` when Docker Desktop sends a Windows notification asking about the shared path
   * Note: If Windows notifications are turned off, you must add each path manually in Docker Desktop (Settings -> Resources -> File Sharing) 

### NextCloud
If NextCloud is used with a shared path, you will see this error upon logging in:
   ```
    Your data directory is readable by other users
    Please change the permissions to 0770 so that the directory cannot be listed by other users.
   ```
Open `/config/config.php` and add the line `'check_data_directory_permissions' => false`  to bypass the check