# [Docker4Wordpress](https://github.com/wodby/docker4wordpress) <a href="https://github.com/wodby/docker4wordpress"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/WordPress_blue_logo.svg/1200px-WordPress_blue_logo.svg.png" width="30"></a>
## This is [Docker4Wordpress](https://github.com/wodby/docker4wordpress) installation instructions:

Docker4Wordpress is an open-source project [GitHub page](https://github.com/wodby/docker4wordpress) that provides pre-configured `docker-compose.yml` file with images to spin up local environment on Linux, Mac OS X and Windows.

## Requirements ##

* Install PHP
```
sudo apt install php-cli php-curl php-gd php-mbstring php-sqlite3 php-xml
```

* [Install Composer](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-osx)
> Note: The instructions below refer to the [global composer installation](https://getcomposer.org/doc/00-intro.md#globally). You might need to replace `composer` with `php composer.phar` (or similar) for your setup.


* [Install Docker ubuntu](https://docs.docker.com/engine/install/ubuntu/).

* [Docker without `sudo`](https://docs.docker.com/engine/install/linux-postinstall)

* Restart PC 

## Installation ##

**1.** Start a new project:

```
composer create-project wodby/wordpress-composer some-dir --stability dev --no-interaction
```

The `composer create-project` command passes ownership of all files to the project that is created. You should create a new git repository, and commit all files not excluded by the .gitignore file.

**2.** Download and unpack `docker4wordpress.tar.gz` from the [latest stable release](https://github.com/wodby/docker4wordpress/releases) to your project root.

* Go to project root.
```
cd some-dir
```
* Unpack `docker4drupal.tar.gz`

**3.** Delete `docker-compose.override.yml`.

**4.** Ensure database credentials match in your wp-config.php and .env files

**5.** Set up Mariadb volume by uncomment `13` and `15` lines and changing path in `docker-compose.yml` to prevent erasing database after `docker compose down`.

```
volumes:
#      - ./mariadb-init:/docker-entrypoint-initdb.d # Place init .sql file(s) here.
      - ./mariadb-data:/var/lib/mysql # Use bind mount
```

**6.** Uncomment `NGINX_SERVER_ROOT` for Nginx and add `/web` to the end.

**7.** Update [.gitignore](https://github.com/giorgitchanturidze/docker-compose-wordpress-guide/blob/main/.gitignore)

### Congrats you can now run WordPress!
* Run in terminal:
```
docker compose up -d
```

[^Note]: docker compose is newer version of docker-composer.

* Open browser and go to this adress:
 ```
 http://wp.docker.localhost:8000/
```
