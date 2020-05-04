# Trustee Install

## Install Ubuntu Server 18.04 on DigitalOcean

-   Install Docker <https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04>

-   Install Docker Compose <https://www.digitalocean.com/community/tutorials/how-to-install-docker-compose-on-ubuntu-18-04>

-   Run 10 Trustee containers on  4GB RAM/80GB SSD droplet ($20/month)

-   Install traefik load balancer to direct subdomain to each patient container.

With registration - a unique subdomain (as0*) is created

-   Add wildcard (*) subdomain to CName

-   Create directory (as*)  named subdomain

-   Inside directory (as*)  create docker-compose.yml **template** that defines **Patient container**

## Trustee container** consists of

-   Nginx proxy-pass to allow subdomain to have a root (/) pointing to **AS container** and /nosh pointing to **pNOSH container**

-   AS container is: a mariadb container + nginx container + php/laravel container with hieofone-as code

-   pNOSH container is: a mariadb container + nginx container + php/laravel container with nosh2 code

-   Docker secrets prevents HIE of One from being able to access each mariadb container instance

-   Backup container

-   SyncThing container to connect to other devices outside of network for off-site backup

pNOSH mariadb database will have data-at-rest encryption enabled

<https://mariadb.com/kb/en/library/data-at-rest-encryption/>

Docker secrets will protect database user and password, file key management for database encryption as well as MailGun domain and secret.

A DigtialOcean droplet snapshot of "trustee-docker-snapshot" named "trustee-docker-snapshot-base" is used to deploy multiple droplets once 10 containers