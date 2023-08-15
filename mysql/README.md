# MySQL and phpMyAdmin Docker Compose File

This repository provides a basic example of using Docker Compose to set up a MySQL database server and a phpMyAdmin interface for managing the database.

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Usage

1. Clone this repository:

	```bash
	git clone https://github.com/your-username/your-repo-name.git
	cd your-repo-name

2. Create a .env file in the same directory as the docker-compose.yml	file and set your MySQL environment variables:

	```
	MYSQL_ROOT_PASSWORD=example_root_password
	MYSQL_DATABASE=example_database
	MYSQL_USER=example_user
	MYSQL_PASSWORD=example_password

3. Run the following command to start the containers:

	```
	docker-compose up -d

This will start the MySQL and phpMyAdmin containers in the background.

4. Access phpMyAdmin by opening your web browser and navigating to http://localhost:8080. Use the MySQL root credentials you specified in the .env file to log in.

## Configuration

The docker-compose.yml file defines the following services:

### MySQL Service

- Image: mysql:5.7
- Container Name: mysql_db
- Environment Variables:
	- MYSQL_ROOT_PASSWORD: Root password for the MySQL server
	- MYSQL_DATABASE: Default database to be created
	- MYSQL_USER: MySQL user
	- MYSQL_PASSWORD: Password for the MySQL user
- Volumes: Data volume for persistent storage

### phpMyAdmin Service

- Image: phpmyadmin/phpmyadmin
- Container Name: phpmyadmin
- Environment Variables:
	- PMA_HOST: Hostname of the MySQL server
	- PMA_PORT: Port of the MySQL server (default: 3306)
	- MYSQL_ROOT_PASSWORD: Root password for the MySQL server
- Ports: Maps host port 8080 to phpMyAdmin container port 80
- Depends On: Ensures phpMyAdmin starts after MySQL is up and running

## License

This project is licensed under the MIT License.
