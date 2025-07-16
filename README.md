````markdown
# WordPress and Uptime Kuma with Docker

This project uses Docker to run a WordPress instance, a MySQL database for WordPress, and an Uptime Kuma monitoring service. This README provides the necessary steps to get started, manage the services, and clean up the environment.

## Prerequisites

Before you begin, you need to have Docker and Docker Compose installed on your system.

### 1. Install Docker

Docker is required to run the containers. Docker Compose is included with Docker Desktop for Windows and macOS. For Linux, you will need to install it separately.

* **Windows/macOS:** Download and install [Docker Desktop](https://www.docker.com/products/docker-desktop/).
* **Linux:** Follow the official instructions for your distribution to install the [Docker Engine](https://docs.docker.com/engine/install/) and then the [Docker Compose plugin](https://docs.docker.com/compose/install/).

## Getting Started

### 2. Start All Services

To start all the services (WordPress, MySQL, and Uptime Kuma) in the background, navigate to the directory containing the `docker-compose.yml` file and run the following command:

```bash
docker-compose up -d
````

  * `up`: This command builds, (re)creates, starts, and attaches to containers for a service.
  * `-d`: This flag runs the containers in detached mode (in the background).

After running the command, you can access:

  * **WordPress:** `http://localhost:80`
  * **Uptime Kuma:** `http://localhost:3001`

## Managing Containers

You can manage individual containers without affecting the others.

### 3\. Stop the WordPress Container

If you need to stop only the WordPress application container, use the following command. This will stop the `wordpress-app` service but leave the database and Uptime Kuma running.

```bash
docker-compose stop wordpress-app
```

### 4\. Stop the WordPress Database Container

To stop only the MySQL database container (`wordpress-db`), run:

```bash
docker-compose stop wordpress-db
```

**Note:** Stopping the database will make your WordPress site unavailable.

## Cleanup

### 5\. Stop and Remove All Resources

To stop all running services and remove the containers, networks, and volumes created by `docker-compose up`, use the `down` command.

```bash
docker-compose down --volumes
```

  * `down`: Stops and removes containers, networks, and images created by `up`.
  * `--volumes`: This flag removes the named volumes (`db_data` and `uptime-kuma-data`) that were created to persist data. **Warning: This will permanently delete your WordPress database and Uptime Kuma data.** If you want to keep the data, omit the `--volumes` flag.

<!-- end list -->

```
```
