# Wordpress-Docker setup

## How to use?

- Cone the repo `git@github.com:aslamdoctor/docker-wordpress.git`
- Run `docker compose up -d`
- Deleted files in your `wordpress` directory and replace with your project if required. Do not replace `wp-config.php` file.
- Run `http://localhost:8000/`
- Follow instructions on screen for installation process
- Run WP-CLI commands like this `docker-compose run --rm wp-cli --info`

## Notes

For best performance on Windows, run your source directory from WSL2 (Win Pro license might be required).
