---
layout: post
title: Deploying Applications Using Nginx and Docker
date: 2025-03-09
description: A beginner-friendly guide to deploying a Next.js frontend, FastAPI backend, and PostgreSQL database using Docker and Nginx.
tags: deployment, docker
categories: devops, web-development
---

## Introduction

Deploying web applications can be overwhelming, especially when handling multiple services like a frontend, backend, and database. This guide will walk you through deploying a **Next.js frontend**, **FastAPI backend**, and **PostgreSQL database** using **Docker** and **Nginx as a reverse proxy**.

By the end of this tutorial, you'll understand how to:
- Use **Docker Compose** to manage multi-container applications.
- Configure **Nginx** as a reverse proxy for your frontend and backend.
- Secure your application with **SSL certificates**.

---

## Understanding the Architecture

We'll deploy the following services:
- **Frontend**: A Next.js application running on port `3000`.
- **Backend**: A FastAPI service running on port `8000`.
- **Database**: A PostgreSQL instance for data storage.
- **Nginx**: A reverse proxy to handle traffic and SSL termination.

Docker Compose will orchestrate these services and ensure they run together in an isolated network.

---

## Step 1: Setting Up Docker Compose

Our **docker-compose.yml** file defines how all the services run together:

```yaml
version: '3.8'

services:
  app:
    image: <link_to_image>
    container_name: fastapi_app
    restart: always
    ports:
      - "8000:8000"
    depends_on:
      - db
    environment:
      - DATABASE_URL=postgresql://${DATABASE_USERNAME}:${DATABASE_PASSWORD}@${DATABASE_HOST}:${DATABASE_PORT}/${DATABASE_NAME}
    networks:
      - app_network

  db:
    image: postgres:latest
    container_name: postgres_db
    restart: always
    environment:
      POSTGRES_USER: ${DATABASE_USERNAME}
      POSTGRES_PASSWORD: ${DATABASE_PASSWORD}
      POSTGRES_DB: ${DATABASE_NAME}
    volumes:
      - postgres_data:/var/lib/postgresql/data
    networks:
      - app_network

  nginx:
    image: nginx:latest
    container_name: nginx_proxy
    restart: always
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf:ro
      - /etc/letsencrypt/<path>/fullchain.pem:/etc/letsencrypt/live/<path>/fullchain.pem
      - /etc/letsencrypt/<path>/privkey.pem:/etc/letsencrypt/live/<path>/privkey.pem
    depends_on:
      - app
    networks:
      - app_network

  frontend:
    image: <link_to_image>
    container_name: nextjs_frontend
    ports:
      - "3000:3000"
    environment:
      - NEXT_PUBLIC_API_URL=<api_url>
    depends_on:
      - app
    networks:
      - app_network

networks:
  app_network:

volumes:
  postgres_data:
```

---

## Step 2: Configuring Nginx as a Reverse Proxy

The Nginx configuration file (**nginx.conf**) routes requests to the correct service:

```nginx
http {
    server {
        listen 80;
        server_name <url>;
        return 301 https://$host$request_uri;
    }

    server {
        listen 443 ssl;
        server_name <url>;
        
        ssl_certificate /etc/letsencrypt/<path>/fullchain.pem;
        ssl_certificate_key /etc/letsencrypt/<path>/privkey.pem;

        location / {
            proxy_pass http://fastapi_app:8000;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        }
    }
}
```

---

## Step 3: Running the Application

### Build and Run the Containers
```bash
docker-compose up -d
```
This will start all services in the background.

### Verify Everything is Running
```bash
docker ps
```
You should see containers for `nginx_proxy`, `fastapi_app`, `nextjs_frontend`, and `postgres_db`.

### Restarting a Service
If you make changes, restart a specific service:
```bash
docker-compose restart nginx
```

---

## Conclusion

You’ve successfully deployed a **Next.js + FastAPI application with PostgreSQL**, managed with **Docker and Nginx**. This setup ensures:
✅ Scalable and isolated services.
✅ Secure deployment with HTTPS.
✅ Easy container management using Docker Compose.

Now, you can focus on developing your application while Docker and Nginx handle the deployment. 🚀