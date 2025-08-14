# HAProxy Load Balancer with Docker Compose

This project demonstrates a simple HAProxy load balancing setup with two Nginx backend servers using Docker Compose.

## Overview

- HAProxy acts as a load balancer distributing traffic between two Nginx servers
- Round-robin balancing algorithm
- Includes HAProxy stats page for monitoring
- Dockerized environment for easy setup

## Prerequisites

- Docker installed
- Docker Compose installed

## Project Structure
haproxy/

├── docker-compose.yml # Docker Compose configuration

├── haproxy.cfg # HAProxy configuration

├── nginx1.conf # Nginx configuration for server 1

├── nginx2.conf # Nginx configuration for server 2

├── html1/ # HTML content for server 1

│ └── index.html

├── html2/ # HTML content for server 2

│ └── index.html

└── README.md # This file


## Configuration Details

### HAProxy
- Listens on port 80 for incoming HTTP traffic
- Stats page available on port 8080 (credentials: admin/admin123)
- Round-robin load balancing between two Nginx servers
- Health checks enabled for backend servers

### Nginx Servers
- Two independent Nginx containers
- Each serves a simple HTML page identifying the server
- Custom configurations mounted via volumes

## Getting Started

1. Clone this repository:
   git clone https://github.com/IHRahimi/linux.git
   cd haproxy


2. Start the containers:
    docker compose up -d

### Access the services:
    
    Load balanced application: http://localhost
    
    HAProxy stats page: http://localhost:2000 (username: admin, password: admin123)


### Verification
    Refresh the application page (http://localhost) multiple times - you should see responses alternating between "Nginx Server 1" and "Nginx Server 2"
    
    Check the stats page to see the backend servers' status and traffic distribution

### Customization
    To change the load balancing algorithm, modify the balance directive in haproxy.cfg
    
    To add more backend servers:
    
    Add new services in docker-compose.yml
    
    Add corresponding server entries in haproxy.cfg
    
    Create new Nginx configuration and HTML content directories

### Clean Up
To stop and remove all containers:

    docker compose down
