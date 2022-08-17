# Wordpress-Docker setup

## How to use?

- Clone the repo `git@github.com:aslamdoctor/docker-wordpress.git`
- Update `.env` file for project credentials
- Run `docker compose up -d`
- Deleted files in your `wordpress` directory and replace with your project if required. Do not replace `wp-config.php` file.
- Run `http://localhost:8000/` for frontend
- Follow instructions on screen for installation process
- Run WP-CLI commands like this `docker-compose run --rm wp-cli --info`
- Run `http://localhost:6060/` for phpMyAdmin

## Some important commands

- To Search-Replace URL in database

  `docker-compose run --rm wp-cli search-replace 'http://mywebsite.local' 'http://mywebsite.local:8000'`

- To backup database from Docker container

  `docker exec CONTAINER_ID mysqldump -u wordpress -pwordpress wordpress --no-tablespaces > ./database.sql`

- To restored database to Docker container

  `docker exec CONTAINER_ID mysql -u wordpress -pwordpress -e "CREATE DATABASE IF NOT EXISTS wordpress"`

  `cat database.sql | docker exec -i CONTAINER_ID /usr/bin/mysql -u wordpress --password=wordpress wordpress`

- To log into Docker container shell

  `docker exec -ti CONTAINER_ID sh`

## Apply proper file/folder permissions to modify the WordPress files

1. Create docker group if not exists. First check if `docker` group exists by typing command `groups`

   `sudo usermod -aG docker $USER`

2. Add write permission to the project volume/folder

   `sudo chmod 775 -R wordpress/wp-content/`

## Notes

For best performance on Windows, run your source directory from WSL2 (Win Pro license might be required).
