# docker-fulcrum
A Docker container for running a [Fulrum server](https://github.com/cculianu/Fulcrum).

## Install
These instructions assume you are using Docker installed on Ubuntu 18.04.

- Clone the repo: `git clone https://github.com/christroutner/docker-fulcrum && cd docker-fulcrum`

### Generate a self-signed certificate
- `sudo apt update`
- `sudo apt install apt-get install openssl`
- `openssl genrsa -des3 -out server.pass.key 2048`
- `openssl rsa -in server.pass.key -out server.key`
- `rm server.pass.key`
- `openssl req -new -key server.key -out server.csr`
- `openssl x509 -req -sha256 -days 365 -in server.csr -signkey server.key -out server.crt`

### Build the Docker Container
- Update the `docker-compose.yml` file with the path to where you want to store the blockchain.
- `docker-compose build`
- `docker-compose up -d`
