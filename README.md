# Project description 

The project mail-mock is docker-compose based tool for developers. It mocks a imap and smtp server and expose a real webmail to consult and send mails. 

# Quick start

To start mail and webmail server, use docker-compose

```bash
$ docker-compose --env-file .env.sample up --build -d
Creating network "mail_mail_network" with driver "bridge"
Building mail-server
Step 1/4 : FROM greenmail/standalone:1.6.1
 ---> 002988723ad0
Step 2/4 : USER root
 ---> Using cache
 ---> 31396ac5ceea
Step 3/4 : RUN apt-get update && apt-get install -y netcat
 ---> Using cache
 ---> 250b77d123e1
Step 4/4 : USER greenmail
 ---> Using cache
 ---> b7fe8bf6971e

Successfully built b7fe8bf6971e
Successfully tagged mail_mail-server:latest
Creating webmail-server ... done
Creating mail-server    ... done

```

You can access to webmail on url http://localhost:8000/. You can access to any mail address. At first connexion, you can define password for each mail address. 

# Docker services

The project contains only one file : *docker-compose.yml*. Two services are declared : 

* **mail-server :** it is the imap and stmp mock server. It uses [greenmail/standalone docker image](https://hub.docker.com/r/greenmail/standalone/). 
* **webmail-server :** it is real webmail server. It is configured to use the mail server. It uses [roundcube/roundcubemail docker image](https://hub.docker.com/r/roundcube/roundcubemail/). 

# Configure 

To configure the addresses and ports of the servers, environment variables are used. An .env.sample file is provided as an example.

| variable | default value | description |
| --- | --- | --- |
| WEBMAIL_HOSTNAME | webmail.myhost.com | webmail hostname on docker network |
| WEBMAIL_PORT | 8000 | webmail exposition port |
| IMAP_SERVER_HOSTNAME |imap.myhost.com | imap server hostname on docker network | 
| IMAP_SERVER_PORT | 3143 | imap server exposition port | 
| SMTP_SERVER_HOSTNAME | smtp.myhost.com | smtp server hostname on docker network | 
| SMTP_SERVER_PORT | 3025 | smtp server exposition port| 
| MAIL_SERVER_HOSTNAME | mail.myhost.com | mock mail ( imap & smtp ) server hostname on docker network. It is using for mail service hostname on docker |




 

