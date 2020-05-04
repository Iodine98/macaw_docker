# Macaw on Docker
This is a multi-container Docker application, [Docker Desktop](https://www.docker.com/products/docker-desktop) is required to run [Macaw](https://github.com/microsoft/macaw). As of now, this application **does not** start Macaw. It installs all dependencies to run Macaw and creates and interactive environment where you can all scripts pertaining to Macaw.

The application is built on the [docker image](https://hub.docker.com/r/roynirmal/pyndri) for [Pyndri](https://github.com/cvangysel/pyndri) which is a Python interface to the Indri search engine. 

At the moment, this image contains:

- Ubuntu 16.04 LTS
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
1. Open your terminal and clone this repository: `git clone https://github.com/Iodine98/macaw_docker`. 
2. Run `cd macaw_docker`.
3. Run `docker-compose build --no-cache`. This will retrieve the necessary images for Ubuntu, Python3, Indri, Pyndri, Stanford Core NLP and finally Macaw itself; and build the containers for mongo and macaw.
4. Run the following command: `docker-compose up -d` (don't close this terminal)
5. Get the `CONTAINER_ID` for `macaw_docker_app` by running `docker ps -a`. 
6. Get into the interactive mode for executing macaw by running `docker-compose run app /bin/bash`. 
7. Execute `python3 /macaw/macaw/live_main.py` to start the basic Macaw STDIO interface.

8. To close the application, press `Ctrl+A+D` on the terminal.

In this docker image we start off with running a bare-bone version of Macaw using the [WikiPassageQA](https://arxiv.org/pdf/1805.03797.pdf) dataset and `Indri` index. For that we perform the following steps (you do not need to repeat them again, this is already done while building the container during steps 1-8 previously): 
1. Get the dataset from [here](https://ciir.cs.umass.edu/downloads/wikipassageqa/WikiPassageQA.zip). 
2. Extarct it. 
3. Convert the data into [`trectext` format](https://sourceforge.net/p/lemur/wiki/Quick%20Start/) required by `Indri` to index the data. For that we use our [script](https://github.com/roynirmal/convert2trectext.git). The script is a bit hacky for now but will update it soon ;)
4. And then finally build the index using `Indri`. 
5. Index the data using `Indri`: `/indri-5.11/buildindex/IndriBuildIndex -corpus.path=./input_file.txt -corpus.class=trectext -index=/data/index`
The `index` arguments specifies the path where you want to store the index. 
 
 
**Different Macaw implementation**: For this tutorial, I have forked the original [Macaw repository](https://github.com/microsoft/macaw) and changed the `./macaw/live_main.py` to the run the bare-bone macaw which retrieve documents from the query we put in the standard input. To have your own implementation (e.g. to activate the voice search feature of macaw using a telegram token or using `bing` instead of `indri` you need to first create a new branch and update the `live_main.py` as requried. Then you need to change the bracnh in the `./docker-images/app/Dockerfile/` image and build the container as in step 3 of 'First Time'. 

**Different dataset**: To download your own dataset (and convert it to the requried format) change the code in `./docker-images/app/Dockerfile/` where I download the dataset using `wget`.





