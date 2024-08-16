Siin on juhend Docker Compose'i konfiguratsioonile vastava rakenduse käivitamiseks:

# Cosmos Odyssey Docker Compose Guide

This guide will help you set up and run the Cosmos Odyssey application using Docker Compose. The application consists of multiple services: a PostgreSQL database, the core backend service, and the frontend service. All these services are defined in the provided `docker-compose.yml` file.

## Prerequisites

Make sure you have Docker and Docker Compose installed on your machine.

- [Install Docker](https://docs.docker.com/get-docker/)
- [Install Docker Compose](https://docs.docker.com/compose/install/)

## Getting Started

### Step 1: Clone the Docker Compose Repository

Clone the repository that contains the Docker Compose configuration:

```bash
git clone https://github.com/kenbockler/cosmos-odyssey-docker.git
```

Navigate to the cloned directory:

```bash
cd cosmos-odyssey-docker
```

### Step 2: Build and Start the Containers

To build the images (if not already built) and start the services defined in the `docker-compose.yml` file, run:

```bash
docker-compose up --build
```

This command will:

- Build the Docker images for the services if they are not already available.
- Start all the services: PostgreSQL database, the core backend server, and the frontend server.
- Expose the services on the specified ports.

### Step 3: Access the Application

Once the services are up and running, you can access the application:

- **Frontend**: The frontend application is accessible at [http://localhost](http://localhost).
- **Backend**: The backend API is accessible at [http://localhost:9090](http://localhost:9090).

### Services Overview

- **PostgreSQL Database**:
    - The PostgreSQL database runs on port `5432`.
    - The container is named `postgres-container`.
    - The database credentials are defined in the environment variables.

- **Core Backend Service**:
    - The backend service runs on port `9090`.
    - The container is named `cosmos-odyssey-core`.
    - It connects to the PostgreSQL database using the provided environment variables.

- **Frontend Service**:
    - The frontend service runs on port `80`.
    - The container is named `cosmos-odyssey-frontend`.
    - This service provides the user interface for interacting with the Cosmos Odyssey application.

### Step 4: Stop the Services

To stop the running services, use the following command:

```bash
docker-compose down
```

This will stop and remove the containers, networks, and volumes created by `docker-compose up`.

### Troubleshooting

- **Container Logs**:
    - You can view the logs of a specific container using:
      ```bash
      docker-compose logs <service_name>
      ```
      Replace `<service_name>` with `postgres`, `core`, or `frontend` to see the respective logs.

- **Restarting Services**:
    - If you need to restart a specific service, you can use:
      ```bash
      docker-compose restart <service_name>
      ```

### Additional Notes

- **Data Persistence**: The PostgreSQL data is stored in a Docker volume named `postgres-data`. This ensures that the database data persists even if the container is stopped or removed.
- **Network**: All services are connected through a Docker network named `cosmos-network`, which allows the services to communicate with each other.
