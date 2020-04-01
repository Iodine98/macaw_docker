# Macaw on Docker
This is a multi-container Docker application, [Docker Desktop](https://www.docker.com/products/docker-desktop) is required to run Macaw.


## Instructions
First Time:
1. Download (or clone) this repository, and unzip the files. 
2. Open a terminal and go to the folder location
3. Run the following command: `docker-compose up --build` (don't close this terminal)
4. This will retrieve the necessary images for Mongo, Redis, Puppeteer, Etherpad, Backend and Frontend; and build the containers
5. You can open the application in your browser in `localhost:8080`
6. To close the application, press `Ctrl+C` on the terminal

The process to re-open the application with the stored data is very similar:
1. Open a terminal and go to the folder location
2. Run the following command: `docker-compose up` (don't close this terminal)
3. Docker will start the pre-built containers
4. You can open the application in your browser in `localhost:8080`
5. To close the application, press `Ctrl+C` on the terminal
