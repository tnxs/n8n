# n8n Docker Setup

This repository contains the Docker setup for running [n8n](https://n8n.io/), an open-source workflow automation tool.

## Prerequisites

- Docker
- Docker Compose

## Getting Started

1. Clone the repository:

   ```sh
   git clone <repository-url>
   cd <repository-directory>
   ```

2. Create a `.env` file in the [n8n](http://_vscodecontentref_/0) directory with the following environment variables:

   ```env
   GENERIC_TIMEZONE=Europe/Berlin
   N8N_BASIC_AUTH_ACTIVE=true
   N8N_BASIC_AUTH_USER=yourUsername
   N8N_BASIC_AUTH_PASSWORD=yourPassword
   WEBHOOK_TUNNEL_URL=https://your-webhook-url.com
   NODE_ENV=production
   EXECUTIONS_MODE=queue
   DB_TYPE=sqlite
   N8N_PORT=5678
   ```

3. Start the Docker containers:

   ```sh
   docker-compose up -d
   ```

4. Access n8n:

   Open your browser and go to `http://localhost:5678` (or the port you specified in the `.env` file).

## Services

- **n8n**: The main n8n service.
- **redis**: Redis service used by n8n for queue management.

## Volumes

- `./n8n_data:/home/node/.n8n`: This volume is used to persist n8n data.

## Networks

- `n8n_network`: A bridge network for communication between the n8n and redis services.

## Stopping the Services

To stop the services, run:

```sh
docker-compose down
```
