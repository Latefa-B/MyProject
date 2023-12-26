# Deployment of a static web page in Apache web server
In this project, we are going to automate the deployment of a static web page in Apache web server. The process involves : **building the environment infrastructure** : AWS EC2 instances, then **Automating an html code that will be deployed on multiple servers**.

The purpose of the project is to deploy a web page and automate it multiple times on multiple servers, using : 
- ssh for a secure connection 
- Apache as a web server software to serve the web page
- a shell script to create the index html file on multiple servers
- Ansible configuration management tool for automation.

During the process we will : 
- Build the environment infrastructure : using AWS EC2 instances, we will create one ansible control node and two target nodes.
- Update the package manager : apt-get and install apache web server software on the servers.
- configurate : start and enable apache web server, create an HTML index file in the web server root directory using a shell script, that contains the code that will be deployed on the web page. We will open the ubuntu firewall to allow traffic on http port 80 then add it as rule in EC2 instances as well. 
- Test and validate the service : we will validate the status of the Apache web server that is running on the target nodes, then test the web page on a web browser using the public IP of the node.
- Publish the project : after completing the project, it will be published and shared using the Git virtual control system and an SSH key pair, on the Github platform. 

## Part I: Building the project 
Below are the steps that i have taken to complete the project: 

<img width="1153" alt="project_step1" src="https://github.com/Latefa-B/MyProject/assets/151809027/ae551c4c-c515-4625-ad29-9d274983c5b2">
