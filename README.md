Local EC2
Run an EC2-like environment locally using Docker.

Guide
This guide assumes you have Docker installed and accessible from your command line.

Setup
Clone the repository:

git clone https://github.com/kartikvermaa/docker-ec2
Navigate to the project directory:

cd local-ec2
Launch the instance (this may take a few minutes):

docker compose up --build -d
SSH into the container:

ssh ubuntu@127.0.0.1 -p 3022
Default password: password

To stop the container:

docker compose down
Add the -v flag to delete the associated volume on the host.

Usage
This container simulates a remote server environment. You can clone repositories containing backend code and run them inside this virtual server.

To expose ports from your backend:

Edit the EXPOSE command in the Dockerfile:

EXPOSE 22 80 443 [YOUR_PORT]
Add the port to the ports directive in the docker-compose.yml file:

ports:
  - "3022:22"
  - "80:80"
  - "443:443"
  - "[HOST_PORT]:[CONTAINER_PORT]"
It comes with docker pre-installed btw, please use sudo while invoking it.

Configuration
The default password for the ubuntu user is password. You can change this in the Dockerfile.
Adjust compute limits in the docker-compose.yml file. The current setup mimics a t2.micro instance.
API (optional)
This also includes a AWS API if you need it for some reason.

Go to api folder by doing cd ./api.
Install the requirements by running pip install -r requirements.txt.
Run the API server using python api.py.
API docs will be released soon.
Roadmap
Implement EC2 API compatibility.
Frontend Interface to do all this.
SSH via browser because why not.
Develop a custom Elastic Kubernetes Service.
Render AWS out of business.
