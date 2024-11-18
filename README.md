# ONE Record on your computer

Welcome to the ONE Record Localhost, in this document you will find all the instructions to run a NE:ONE server in your local machine.

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/) installed
- [Git](https://git-scm.com/downloads) installed

## Step by step guide

1) Clone the repository
   ```bash
   git clone https://github.com/astein-iamovers/neone-localhost
   ```
2) Switch to the directory to docker-compose
   ```bash
   cd neone-localhost
   ```
   If you have Mac or Linux, please reset folder permissions 
   ```bash
   chmod -R 755 ./
   ```
4) Start all services with [docker compose](https://docs.docker.com/compose/)
   ```bash
   docker compose up -d
   ```
5) Wait until all containers are up and running:
   ```bash
   [+] Running 6/6
    ✔ Network docker-compose_default            Created 0.0s 
    ✔ Container docker-compose-graph-db-1       Healthy 0.0s 
    ✔ Container docker-compose-keycloak-1       Healthy 0.0s 
    ✔ Container docker-compose-ne-one-server-1  Started 0.0s 
    ✔ Container docker-compose-graph-db-setup-1 Started 0.0s
   ```
6) Try to access the ONE Record Server by  http://localhost:8080 using your favorite browser. 
   You should see a HTTP Error 401, because you did not authenticate yet. But this confirms that the ONE Record Server is up and running.

# Overview of services

| Name | Description | Base URL / Admin UI |
|-|-|-|
| ne-one-1 | [ne-one server](https://git.openlogisticsfoundation.org/wg-digitalaircargo/ne-one) | http://localhost:8080 |
| ne-one view | [ne-one view](https://git.openlogisticsfoundation.org/wg-digitalaircargo/ne-one-view) | http://localhost:3000 |
| ne-one play | [ne-one play](https://github.com/aloccid-iata/neoneplay) | http://localhost:3001 |
| graphdb | GraphDB database as database backend for ne-one-server using repository neone | http://localhost:7200 |
| keycloak | Identity provider to authenticate ONE Record clients and to obtain tokens for outgoing requests. <br/> **Preconfigured client_id:** neone-client<br/> **Preconfigured client_secret:** lx7ThS5aYggdsMm42BP3wMrVqKm9WpNY  | http://localhost:8989 <br/> (username/password: admin/admin)|
| notification-handler | A simple Flask app that listens on port 5001 for incoming notifications| http://localhost:5001 |

IMPORTANT: To simplify the setup, both NE:ONE servers are connected to a single Keycloak server, sharing the same user account.

## Add NE:ONE server into NE:ONE Play

1. Connect to NE:ONE Play http://localhost:3001 

2. Click on the setting button in the top-right corner (cog icon)

3. Add your ne-one-server server following this instruction:

    - Organization Name: <Choose a name (any string is accepted)>
    - Protocol: http
    - Host: http://localhost:8080  
    - Token : <Use the postman collection to generate a token and copy it here (follow the previous paragraph)>
    - Color : pick up a random color

4. Now you can start using NE:ONE Play. 

