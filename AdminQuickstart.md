layout: page
title: "Admin Quickstart"
permalink: /about/AdminQuickstart/

# Overview
Administrator Quickstart for Installing with Docker and Using ownCloud.

# Prerequisite
[Docker installation](https://www.cyberciti.biz/faq/install-use-setup-docker-on-rhel7-centos7-linux/) should be completed on your desktop.

# Installing with Docker

## Table of Contents

* [Introduction](#Introduction)
* [Docker Compose](#Docker-Compose)
  * [Logging In](#Logging-In)
  * [Stopping the Containers](#Stopping-the-Containers)
  * [Running occ Commands](#Running-occ-Commands)
  * [Docker Compose YAML File](#Docker-Compose-YAML-File)
* [Troubleshooting](#Troubleshooting)
  * [Raspberry Pi](#Raspberry-Pi)

## Introduction

ownCloud can be installed using the [official ownCloud Docker image](http://https://hub.docker.com/r/owncloud/server). This official image is designed to be used in a docker-compose setup.

You can add certain users to the group <code>docker</code> to grant them docker command rights.

<code>sudo usermod -aG docker &lt;your-user&gt;</code>

*Note:*
>
>* The changes via <code>usermod</code> take effect after the docker users log in. You can reboot or log in again to run docker commands.
>* Users not added to the <code>docker</code> group can run docker commands with a preceding <code>sudo</code>. 

## Docker Compose

#### The Configuration

* Exposes port 8080, that allows HTTP connections.
* Uses separate MariaDB and Redis containers.
* Mounts the data and MySQL data directories on the host for persistent storage.

#### Installation

Follow these instructions for local installation.

*Note:*
>
>You must adapt the value of OWNCLOUD_DOMAIN for remote access.

1. Create a new project directory.
2. Copy and paste the sample <code>docker-compose.yml</code> from this page into the new directory.
3. Create a <code>.env</code> configuration file, which contains the required configuration settings.

<table class="tableblock frame-all grid-all stretch">
<colgroup>
<col style="width: 25.7142%;">
<col style="width: 28.5714%;">
<col style="width: 45.7144%;">
</colgroup>
<thead>
<tr>
<th class="tableblock halign-left valign-top">Setting Name</th>
<th class="tableblock halign-left valign-top">Description</th>
<th class="tableblock halign-left valign-top">Example</th>
</tr>
</thead>
<tbody>
<tr>
<td class="tableblock halign-left valign-top"><p class="tableblock"><code>OWNCLOUD_VERSION</code></p></td>
<td class="tableblock halign-left valign-top"><p class="tableblock">The ownCloud version</p></td>
<td class="tableblock halign-left valign-top"><p class="tableblock"><code>latest</code></p></td>
</tr>
<tr>
<td class="tableblock halign-left valign-top"><p class="tableblock"><code>OWNCLOUD_DOMAIN</code></p></td>
<td class="tableblock halign-left valign-top"><p class="tableblock">The ownCloud domain</p></td>
<td class="tableblock halign-left valign-top"><p class="tableblock"><code>localhost:8080</code></p></td>
</tr>
<tr>
<td class="tableblock halign-left valign-top"><p class="tableblock"><code>ADMIN_USERNAME</code></p></td>
<td class="tableblock halign-left valign-top"><p class="tableblock">The admin username</p></td>
<td class="tableblock halign-left valign-top"><p class="tableblock"><code>admin</code></p></td>
</tr>
<tr>
<td class="tableblock halign-left valign-top"><p class="tableblock"><code>ADMIN_PASSWORD</code></p></td>
<td class="tableblock halign-left valign-top"><p class="tableblock">The admin user’s password</p></td>
<td class="tableblock halign-left valign-top"><p class="tableblock"><code>admin</code></p></td>
</tr>
<tr>
<td class="tableblock halign-left valign-top"><p class="tableblock"><code>HTTP_PORT</code></p></td>
<td class="tableblock halign-left valign-top"><p class="tableblock">The HTTP port to bind to</p></td>
<td class="tableblock halign-left valign-top"><p class="tableblock"><code>8080</code></p></td>
</tr>
</tbody>
</table>

Start the container, using your preferred Docker *command-line tool*. The example below shows how to use [Docker Compose](https://docs.docker.com/compose/).

>### Create a new project directory
>mkdir owncloud-docker-server
>  
>cd owncloud-docker-server
>
>#### Copy docker-compose.yml from the GitHub repository
>wget https://raw.githubusercontent.com/owncloud/docs/master/modules/admin_manual/examples/installation/docker/docker-compose.yml
>
>#### Create the environment configuration file
>cat << EOF > .env<br>
>OWNCLOUD_VERSION=10.8<br>
>OWNCLOUD_DOMAIN=localhost:8080<br>
>ADMIN_USERNAME=admin<br>
>ADMIN_PASSWORD=admin<br>
>HTTP_PORT=8080<br>
>EOF<br>
>
>#### Build and start the container
>docker-compose up -d

After the process completes, run <code>docker-compose ps</code> to check if all the containers have successfully started.<br>
You should see output similar to the one below:

<table class="tableblock frame-all grid-all stretch">
<colgroup>
<col style="width: 18.75%;">
<col style="width: 31.25%;">
<col style="width: 18.75%;">
<col style="width: 31.25%;">
</colgroup>
<thead>
<tr>
<th class="tableblock halign-left valign-top">Name</th>
<th class="tableblock halign-left valign-top">Command</th>
<th class="tableblock halign-left valign-top">State</th>
<th class="tableblock halign-left valign-top">Ports</th>
</tr>
</thead>
<tbody>
<tr>
<td class="tableblock halign-left valign-top"><p class="tableblock">owncloud_mariadb</p></td>
<td class="tableblock halign-left valign-top"><p class="tableblock">docker-entrypoint.sh --max &#8230;&#8203;</p></td>
<td class="tableblock halign-left valign-top"><p class="tableblock">Up (healthy)</p></td>
<td class="tableblock halign-left valign-top"><p class="tableblock">3306/tcp</p></td>
</tr>
<tr>
<td class="tableblock halign-left valign-top"><p class="tableblock">owncloud_redis</p></td>
<td class="tableblock halign-left valign-top"><p class="tableblock">docker-entrypoint.sh --dat &#8230;&#8203;</p></td>
<td class="tableblock halign-left valign-top"><p class="tableblock">Up (healthy)</p></td>
<td class="tableblock halign-left valign-top"><p class="tableblock">6379/tcp</p></td>
</tr>
<tr>
<td class="tableblock halign-left valign-top"><p class="tableblock">owncloud_server</p></td>
<td class="tableblock halign-left valign-top"><p class="tableblock">/usr/bin/entrypoint /usr/b &#8230;&#8203;</p></td>
<td class="tableblock halign-left valign-top"><p class="tableblock">Up (healthy)</p></td>
<td class="tableblock halign-left valign-top"><p class="tableblock">0.0.0.0:8080&#8594;8080/tcp</p></td>
</tr>
</tbody>
</table>

The database, ownCloud and Redis containers are running, and that ownCloud is accessible via port 8080 on the host machine.

***IMPORTANT***
>
>All files stored in this setup are contained in Docker volumes and the admin is responsible to make the files persistent.
>
>To inspect the volumes run:
>
><code>docker volume ls | grep ownclouddockerserver</code>
>
>To export the files as a tar archive run:
>
><code>docker run -v ownclouddockerserver_files:/mnt \
>            ubuntu tar cf - -C /mnt . > files.tar</code>

*Tip*
>
>It may take a few minutes for ownCloud to be fully functional.<br>
>To inspect the log output:
>
><code>docker-compose logs --follow owncloud</code>
>
>Wait until the output shows **Starting apache daemon…** before you access the web UI.

***IMPORTANT***
>Although all important data persists after:
>
><code>docker-compose down; docker-compose up -d</code>
>
>there are certain details that get lost.<br>
>For example, default apps may re-appear after they were uninstalled.

### Logging In

1. Open <code>http://localhost:8080</code> in your browser to log in to the ownCloud UI. The standard ownCloud login screen opens.

![OwnCloud Login Page](https://github.com/satyajeetmunje/satyajeetmunje.github.io/blob/main/Page1.png)

2. Enter username and password which you stored in <code>.env</code> earlier.

*Note*
>Login credentials will not change between deploys even if you change the values in .env.

### Stopping the Containers

To stop the containers using docker compose:

<code>docker-compose stop</code>

To stop and remove containers along with the related networks, images and volumes:

<code>docker-compose down --rmi all --volumes</code>

### Running occ Commands

To run an occ command, go to the directory where your <code>.yaml</code> or <code>.env</code> file is located. Here, you can run any command referring to [Using the occ Command](https://doc.owncloud.org/server/10.7/admin_manual/configuration/server/occ_command.html) by entering:

<code>docker-compose exec owncloud occ <command></code>

***IMPORTANT***
>
>It is advisable not to use the php command prefix in docker environments.

### Docker Compose YAML File

The file <code>docker-compose.yml</code> contains the configuration of your ownCloud container.

*Note*
>
>All supported enterprise features and apps are included in the public image owncloud/server available on Docker Hub. 

YAML

<div class="listingblock">
<div class="content">
<pre class="highlightjs highlight"><code class="language-yaml hljs" data-lang="yaml">version: "3"
<br>

volumes:
  files:
    driver: local
  mysql:
    driver: local
  redis:
    driver: local

services:
  owncloud:
    image: owncloud/server:${OWNCLOUD_VERSION}
    container_name: owncloud_server
    restart: always
    ports:
      - ${HTTP_PORT}:8080
    depends_on:
      - mariadb
      - redis
    environment:
      - OWNCLOUD_DOMAIN=${OWNCLOUD_DOMAIN}
      - OWNCLOUD_DB_TYPE=mysql
      - OWNCLOUD_DB_NAME=owncloud
      - OWNCLOUD_DB_USERNAME=owncloud
      - OWNCLOUD_DB_PASSWORD=owncloud
      - OWNCLOUD_DB_HOST=mariadb
      - OWNCLOUD_ADMIN_USERNAME=${ADMIN_USERNAME}
      - OWNCLOUD_ADMIN_PASSWORD=${ADMIN_PASSWORD}
      - OWNCLOUD_MYSQL_UTF8MB4=true
      - OWNCLOUD_REDIS_ENABLED=true
      - OWNCLOUD_REDIS_HOST=redis
    healthcheck:
      test: ["CMD", "/usr/bin/healthcheck"]
      interval: 30s
      timeout: 10s
      retries: 5
    volumes:
      - files:/mnt/data

  mariadb:
    image: mariadb:10.5
    container_name: owncloud_mariadb
    restart: always
    environment:
      - MYSQL_ROOT_PASSWORD=owncloud
      - MYSQL_USER=owncloud
      - MYSQL_PASSWORD=owncloud
      - MYSQL_DATABASE=owncloud
    command: ["--max-allowed-packet=128M", "--innodb-log-file-size=64M"]
    healthcheck:
      test: ["CMD", "mysqladmin", "ping", "-u", "root", "--password=owncloud"]
      interval: 10s
      timeout: 5s
      retries: 5
    volumes:
      - mysql:/var/lib/mysql

  redis:
    image: redis:6
    container_name: owncloud_redis
    restart: always
    command: ["--databases", "1"]
    healthcheck:
      test: ["CMD", "redis-cli", "ping"]
      interval: 10s
      timeout: 5s
      retries: 5
    volumes:
      - redis:/data</code></pre>
</div>
</div>
</div>
</div>
</div>
 
## Troubleshooting

### Raspberry Pi

If your container fails to start on Raspberry Pi or other ARM devices, you may have an old version of <code>libseccomp2</code> on your host. This should affect distros based on Rasbian Buster 32 bit. Install a newer version with the following command:

<div class="listingblock">
<div class="content">
<pre class="highlightjs highlight"><code class="language-console hljs" data-lang="console">cd /tmp
wget http://ftp.us.debian.org/debian/pool/main/libs/libseccomp/libseccomp2_2.5.1-1_armhf.deb
sudo dpkg -i libseccomp2_2.5.1-1_armhf.deb</code></pre>
</div>
</div>

Alternatively, you can add the backports repo for Debian Buster:

<div class="listingblock">
<div class="content">
<pre class="highlightjs highlight"><code class="language-console hljs" data-lang="console">sudo apt-key adv --keyserver keyserver.ubuntu.com \
     --recv-keys 04EE7237B7D453EC 648ACFD622F3D138
echo "deb http://deb.debian.org/debian buster-backports main" | \
     sudo tee -a /etc/apt/sources.list.d/buster-backports.list
sudo apt update
sudo apt install -t buster-backports libseccomp2</code></pre>
</div>
 
You should restart the container after confirming you have <code>libseccomp2.4.4</code> installed.

For more information see: [Linux Server Docs](https://docs.linuxserver.io/faq)


