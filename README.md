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

## Notes

For best performance on Windows, run your source directory from WSL2 (Win Pro license might be required).
