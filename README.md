# legacy-game-docker
  
Local development environment containerized using Docker.  

Clone this repository and run `$ ocker-compose up` to start the development server.  

In addition to this consult the documentation found at codebase.com.

## Database files.

To import a copy of the database during `docker-compose` place the following files in the `mysql/sql/` folder
* legacy_gamedata.sql
* legacy_globaldata.sql
* legacy_tempdb.sql

## PHPMyAdmin

A container of PHPMyAdmin is included in the environment, access it at `localhost:8080`  

## MySQL

Open `docker-compose.yml` to view MySQL credentials.  
To change these edit the file and run `docker-compose up --build`  

At first build a copy of the legacy database will be imported.
*This database will not be updated regularly, always make sure you have the latest content and structure from codebase*  