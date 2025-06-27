# WordPress Docker Setup

A Docker-based WordPress development environment with Traefik reverse proxy support.

## Quick Start

1. **Clone the repository**
   ```bash
   git clone git@github.com:aslamdoctor/docker-wordpress.git
   cd docker-wordpress
   ```

2. **Configure environment**
   - Update the `.env` file with your project credentials

3. **Start the containers**
   ```bash
   docker compose up -d
   ```

4. **Setup WordPress files** (optional)
   - Delete files in your `wordpress` directory and replace with your project files if needed
   - **Important:** Do not replace the `wp-config.php` file

5. **Add hosts entry**
   Add the following to your `/etc/hosts` file:
   ```
   127.0.0.1 mywebsite.local
   ::1 mywebsite.local
   ```

6. **Access your site**
   - **Frontend:** http://mywebsite.local/
   - **Adminer:** http://mywebsite.local:6060/
   - Follow the on-screen WordPress installation instructions

## Traefik Reverse Proxy Setup

1. **Create the Traefik network**
   ```bash
   docker network create traefik
   ```

2. **Start Traefik**
   ```bash
   cd traefik
   docker compose up -d
   ```

## Essential Commands

### WP-CLI Commands

- **Get WP-CLI info**
  ```bash
  docker-compose run --rm wp-cli --info
  ```

- **Search and replace URLs**
  ```bash
  docker compose run --rm wp-cli search-replace 'http://mywebsite.local' 'http://mywebsite.local:8000'
  ```

- **Install essential plugins**
  ```bash
  docker-compose run --rm wp-cli wp plugin install regenerate-thumbnails --activate svg-support --activate duplicate-post --activate contact-form-7 --activate
  ```

### Database Management

- **Export database**
  ```bash
  docker compose run --rm wp-cli wp db export - > database.sql
  ```

- **Import database**
  ```bash
  docker compose run --rm wp-cli wp db import - < database.sql
  ```

- **Backup database from MySQL container**
  ```bash
  docker exec CONTAINER_ID mysqldump -u wordpress -pwordpress wordpress --no-tablespaces > ./database.sql
  ```

- **Restore database to MySQL container**
  ```bash
  docker exec CONTAINER_ID mysql -u wordpress -pwordpress -e "CREATE DATABASE IF NOT EXISTS wordpress"
  cat database.sql | docker exec -i CONTAINER_ID /usr/bin/mysql -u wordpress --password=wordpress wordpress
  ```

### Container Management

- **Access container shell**
  ```bash
  docker exec -ti CONTAINER_ID sh
  ```

## File Permissions Setup

To modify WordPress files properly, set the correct permissions:

1. **Create docker group** (if it doesn't exist)

   First, check existing groups:
   ```bash
   groups
   ```

   Add user to docker group:
   ```bash
   sudo usermod -aG docker $USER
   ```

2. **Set write permissions**
   ```bash
   sudo chmod 775 -R wordpress/wp-content/
   ```

## Performance Notes

For optimal performance on Windows, run your source directory from WSL2 (Windows Pro license may be required).

## Resources

- [Related Article: Docker WordPress Web Development Stack](https://www.aslamdoctor.com/docker-wordpress-web-development-stack/)
