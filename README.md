# Node-RED Blogging App

A basic blogging application using Node-RED, Node-RED Dashboard, and MySQL, all running in Docker containers.

# Features

	•	Create, read, and filter blog posts.
	•	Simple web interface with Node-RED Dashboard.
	•	Dockerized for easy setup.

# Requirements

	•	Docker and Docker Compose

# Installation

     
 ## 1. Create docker-compose.yml file and change Credentials, make sure that the credentials match the mysql node configuration:
	version: '3'
	services:
	      nodered:
		build: .
		ports:
		- "1880:1880"
		volumes:
		- ./data:/data
		depends_on:
		- mysql

	      mysql:
	        image: mysql:latest
	        environment:
	          MYSQL_ROOT_PASSWORD: YourPass
	          MYSQL_DATABASE: Node-DB
	          MYSQL_USER: YOURNAME
	          MYSQL_PASSWORD: YOURPASS
	        ports:
	          - "3307:3306"  
	        volumes:
	          - mysql-data:/var/lib/mysql
 	volumes:
 	mysql-data:
       
## 2. Create "data" folder and create Dockerfile 
	FROM nodered/node-red:latest
	COPY . /data
 

## 3. Start containers:
     docker-compose up -d

## 4.  Access Node-RED:
    Go to http://localhost:1880.
    
## 5.  Install Node-RED nodes:
	•	Open Node-RED.
	•	Go to the menu, select “Manage palette” -> “Install” tab.
	•	Install node-red-dashboard and node-red-node-mysql.
 
 #  Usage
	•	Import the flow: Use the provided blog-node-red.json and make sure MySQL node configuration matches the db and credentials.
	•	Access the Dashboard: Go to http://localhost:1880/ui.
