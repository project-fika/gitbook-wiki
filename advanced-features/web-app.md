---
description: How to install the Fika Web App
---

# Web App

## Introduction

{% hint style="info" %}
While this web app is designed to make server administration easier in the long run, the initial setup and maintenance require advanced technical knowledge.

The application runs as a fully isolated Docker container. To ensure stability and security, proficiency with container technology is essential. If you are strictly looking for a "plug-and-play" solution and are unfamiliar with Docker, this solution may not be the best fit for your needs.

A Windows-based solution is in progress, but is not yet available.
{% endhint %}

## What is the web app?

FikaWebApp is a ReactTS web application designed to help you administrate your server.\
Features included are:

* Creating moderator/admin accounts
* Sending items (supports modded items)
  * Send items to everyone
  * Send items at a specific date
* Flea banning
* Statistics page (WIP)
* Administrate connected headless clients
* Uploading/downloading profiles
* Uploading/downloading files

## Installation

The Docker image can under [packages](https://github.com/orgs/project-fika/packages?repo_name=Fika-Server-CSharp) on the server repository.

Use your preferable way of running the docker image. It's recommended to use the `compose.yml` below as certain variables are required to run the app, unless you are certain of what you are doing.

After running, access the site at `http://localhost:8080/` (unless you use a reverse proxy) and login using the standard account:

* **User**: admin
* **Password**: Admin123!

{% hint style="warning" %}
**Change your password after logging in!**
{% endhint %}

### Example compose

{% code title="compose.yml" fullWidth="false" %}
```yml
services:
  fika-webapp:
    image: ghcr.io/project-fika/fika-webapp:latest
    container_name: fika-webapp
    restart: unless-stopped
    ports:
      - "8080:8080"
    environment:
      - ASPNETCORE_ENVIRONMENT=Production
      - FikaConfig__APIKey=YOUR_API_KEY
      - FikaConfig__BaseUrl=https://localhost:6969
    volumes:
      - ./data:/app/Data
      - ./logs:/app/Logs
```
{% endcode %}

The compose above will let you run the web app, and access it without `https`.\
It is, however, recommended to use a reverse proxy, e.g. Traefik.

Make sure to read all the lines carefully, and change the required variables which are:

1. `API_KEY`
2. `BASE_URL`

## Updating

If you used the compose files above, the volume will automatically be safe when updating. To update, simply re-run the compose and the latest image will be fetched and installed. Your data will be safe in the `webappdata` folder.

If you _**did not use**_ the compose, make sure to backup the entire data folder in `/app/data`!

{% hint style="danger" %}
Failure to use the compose, or backup the folder will result in a _permanent_ data loss after updating!
{% endhint %}
