# Simple Translate App

## Installing App on VM Manually
* Create a VM Instance from [GCP](https://console.cloud.google.com/compute/instances)
* SSH into your newly created instance
* Install Git: `sudo apt install git`
* Clone App Repo: `git clone https://github.com/dlops-io/simple-translate.git`
* `cd simple-translate`
* Install Python: `sudo apt install python3-pip`
* Install packages: `pip3 install googletrans==4.0.0rc1`
Test out the translations:
* `python3 cli.py`
* `python3 cli.py -t "Good morning" -s "en" -d "es"`
* `python3 cli.py -t "Good afternoon" -s "en" -d "fr"`

## Installing App on VM using Pipenv
* Create a VM Instance from [GCP](https://console.cloud.google.com/compute/instances)
* SSH into your newly created instance
* Install Git: `sudo apt install git`
* Clone App Repo: `git clone https://github.com/dlops-io/simple-translate.git`
* `cd simple-translate`
* Install Pipenv: `sudo apt install pipenv`
* Install Pipenv environment from Pipfile: `pipenv install`
* Go into the newly created environment shell: `pipenv shell`
Test out the translations:
* `python cli.py`
* `python cli.py -t "Good morning" -s "en" -d "es"`
* `python cli.py -t "Good afternoon" -s "en" -d "fr"`

## Accessing files from GCS Bucket
* You can download a file from GCS using `https://storage.googleapis.com/ac215-d/tips.md` (path of file in GCS)
* You can upload a file to GCS using `curl --upload-file tips2.md https://storage.googleapis.com/ac215-d/` (provided you have write access)

## Running App on VM using Docker
* Create a VM Instance from [GCP](https://console.cloud.google.com/compute/instances)
* SSH into your newly created instance
Install Docker on the newly created instance by running
* `curl -fsSL https://get.docker.com -o get-docker.sh`
* `sudo sh get-docker.sh`
Check version of installed Docker
* `sudo docker --version`
Run the app using Docker
* `sudo docker run --rm -ti dlops/simple-translate`

## Developing App using Containers

### Prerequisites for Development using Containers
* Have Docker Desktop installed
* Cloned this repository to your local machine with a terminal up and running
* Check that your Docker is running with the following command

`docker run hello-world`


### Install VSCode  
Follow the [instructions](https://code.visualstudio.com/download) for your operating system.  
If you already have a preferred text editor, skip this step.  

### Make sure we do not have any running containers and clear up an unused images
* Run `docker container ls`
* Stop any container that is running
* Run `docker system prune`
* Run `docker image ls`

### Clone the github repository
- Clone or download from [here](https://github.com/dlops-io/simple-translate)

### Building Docker Image
Go into the app folder by running
* `cd simple-translate`
Build the docker container by running
* `docker build -t simple-translate -f Dockerfile .`

### Running Docker Container
Run the container using:
* `docker run --rm -ti simple-translate`
Running the translate code
* `python cli.py -t "Good morning" -s "en" -d "es"`
To exit from container
* Type `exit` from the Docker shell

### Pushing Docker Image to Docker Hub
* Sign up in Docker Hub and create an [Access Token](https://hub.docker.com/settings/security)
* Login to the Hub: `docker login -u <USER NAME> -p <ACCESS TOKEN>`
* Tag the Docker Image: `docker tag simple-translate <USER NAME>/simple-translate`
* Push to Docker Hub: `docker push <USER NAME>/simple-translate`



