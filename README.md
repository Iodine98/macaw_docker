# Macaw on Docker
This is a multi-container Docker application, [Docker Desktop](https://www.docker.com/products/docker-desktop) is required to run [Macaw](https://github.com/microsoft/macaw). As of now, this application **does not** start Macaw. It installs all dependencies to run Macaw and creates and interactive environment where you can all scripts pertaining to Macaw.

The application is built on the [docker image](https://hub.docker.com/r/roynirmal/pyndri) for [Pyndri](https://github.com/cvangysel/pyndri) which is a Python interface to the Indri search engine. 

At the moment, this image contains:

- Ubuntu 18.04 LTS
- Python 3.6.9
- Retrieval back-end systems:
  * Indri 5.11
  * Pyndri 0.4 
- Java 11.0.6
- Stanford Core NLP
- Macaw

The first three images are built in the container for Pyndri. We build the last three on top of that in this macaw docker application. 

## Instructions
First Time:
1. Open your terminal and clone this repository: `git clone https://github.com/roynirmal/macaw_docker`. 
2. Run `cd macaw_docker`.
3. Run the following command: `docker-compose up --build` (don't close this terminal)
4. This will retrieve the necessary images for Ubuntu, Python3, Indri, Pyndri, Stanford Core NLP and finally Macaw itself; and build the containers
5. To start an interactive development environment (with the above mentioned packages installed) that shares a folder with your local (host): `docker run -it -v /host/path:/container/path macaw_docker_app`.

`-it` enables the interactive environment `-v /host/path:/container/path` mounts the volume `/host/path` seen inside the image as `/container/path`
6. To close the application, press `Ctrl+A+D` on the terminal.

The process to re-open the application with the stored data is very similar:
1. Open a terminal and go to the folder location
2. Run the following command: `docker-compose up` (don't close this terminal)
3. Docker will start the pre-built containers
4. You can open the application in the interactive environment with `docker run -it macaw_docker_app`
5. To close the application, press `Ctrl+A+D` on the terminal
