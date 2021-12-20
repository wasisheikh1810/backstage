# DESCRIPTION
A demo project for open platform for building developer portals {build in nodjs} 

# Requirements

For development, you will only need Node.js and a node global package, Yarn, installed in your environement.


# OVERWRITE
Deploy Backstage Standalone with npm packages
Run Backstage Standalone with a PSQLite in-memory database and demo content


# Install Node
- Node installation on Windows

  Just go on [official Node.js website](https://nodejs.org/) and download the installer.
Also, be sure to have `git` available in your PATH, `npm` might need it (You can find git [here](https://git-scm.com/)).

- Node installation on Ubuntu

  You can install nodejs and npm easily with apt install, just run the following commands.

      $ sudo apt install nodejs
      $ sudo apt install npm
      $ node use 16.5.0
-  Other Operating Systems
  You can find more information about the installation on the [official Node.js website](https://nodejs.org/) and the [official NPM website](https://npmjs.org/).

If the installation was successful, you should be able to run the following command.

    $ node --version
    16.5.0

    $ npm --version
    '7.19.1'
    
If you need to update `npm`, you can make it using `npm`! Cool right? After running the following command, just open again the command line and be happy.

    $ npm install npm -g

# Yarn installation
  After installing node, this project will need yarn too, so just run the following command.

    $ npm install -g yarn

# Now Create your Backstage App
To install the Backstage Standalone app, we make use of npx, a tool to run Node executables straight from the registry. This tool is part of your Node.js installation. Running the command below will install Backstage. The wizard will create a subdirectory inside your current working directory.

    $ npx @backstage/create-app

# Run the Backstage app
    $ yarn dev
    $ yarn build
    
- It might take a little while, but as soon as the message [0] webpack compiled successfully appears, you can open a browser and directly navigate to your freshly installed Backstage portal at http://localhost:3000. You can start exploring the demo immediately. Please note that the in-memory database will be cleared when you restart the app

- after the yarn build command all the files are build convinently and after we need to dockerize the app as the command has build all the file it also included the dockerfile as well so we will first install the docker if we dont have it after that we need to run the build command 

    $ docker image build . -f packages/backend/Dockerfile --tag backstage
- we will get a message as 
Successfully built 3a40b870bc44
Successfully tagged backstage:latest

    $ docker images
    for all the iamges we have build 
    
- After this we need to login into the GCP and deploy our app through the GKE
#for this we first need to create an GCP account and create kubernetes cluster and login into it
    Before you begin
If you want to use the command-line do the following:
Install or update to the latest version of the gcloud command-line tool.
Set a default region and zone.

# To initialize the command in Gcloud:
   $ gcloud init [--console-only] [GCLOUD_WIDE_FLAG …]

   $ gcloud auth login
   $ gcloud config set account `ACCOUNT`
   $ gcloud config set project test1-project

- after the login tnto the gke cluster, run the command to apply kubernetes
    $ kubectl create namespace backstage
{this is to create a namecspace in the cluster}

   $ kubectl apply -f kubernetes/
{to apple the YAML we have given}

   $ kubectl get svc --namespace=backstage
{to see all the services}

   $ kubectl get po --namespace=backstage
{to see the pos that has been created}

   $ kubectl get deployment --namespace=backstage
{to finally deploy it to the cluster}













