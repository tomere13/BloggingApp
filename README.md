# Node-RED Blogging App

A basic blogging application using Node-RED, Node-RED Dashboard, and MySQL, all running in Docker containers.

# Features

	•	Create, read, update, and delete blog posts.
	•	Simple web interface with Node-RED Dashboard.
	•	Dockerized for easy setup.

# Requirements

	•	Docker and Docker Compose

# Installation

	1.	Clone the repository: 
     git clone https://github.com/your-username/node-red-blogging-app.git 
     cd node-red-blogging-app
     
 	2.	Create docker-compose.yml file and change Credentials at MySQL (make sure your MySQL server matches db name below):
      version: '3'
      services:
      \nodered:
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
          MYSQL_DATABASE: DB_NAME
          MYSQL_USER: YOURNAME
          MYSQL_PASSWORD: YOURPASS
        ports:
          - "3307:3306"  
        volumes:
          - mysql-data:/var/lib/mysql
    
    volumes:
      mysql-data:

	3.	Start containers:
     docker-compose up -d

  # Access Node-RED:
    Go to http://localhost:1880.
    
  # Install Node-RED nodes:
	•	Open Node-RED.
	•	Go to the menu, select “Manage palette” -> “Install” tab.
	•	Install node-red-dashboard and node-red-node-mysql.
 
  # Usage
	•	Import the flow: Use the provided flows.json.
	•	Access the Dashboard: Go to http://localhost:1880/ui.
