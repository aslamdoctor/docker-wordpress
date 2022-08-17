# Duplicator friendly-ish Wordpress-Docker setup

## How to use?

- create Duplicator package on Wordpress you'd like to duplicate following: [Step 2: Export the WordPress Site](https://www.cloudways.com/blog/wordpress-from-localhost-to-cloudways-using-duplicator/)
- Download Duplicator package and installer
- Install [Docker](https://www.docker.com/)
- Download [docker-compose.yml](https://github.com/LabZoneSK/wordpress-docker-duplicator/blob/master/docker-compose.yml)
- Run `docker compose up --build`
- Deleted files in your `wordpress` directory
- Copy Duplicator files into `wordpress` directory
- Run `http://localhost:8000/wordpress/installer.php`
- Follow instructions on screen
- Run WP-CLI commands like this `docker-compose run --rm wp-cli --info`

## Notes

For best performance on Windows, run your source directory from WSL2 (Win Pro license might be required).
