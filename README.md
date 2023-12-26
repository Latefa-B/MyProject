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

**Step 1: set up the work infrastructure by creating AWS EC2 instances ( one controller node and two target nodes )**
<img width="1153" alt="project_step1" src="https://github.com/Latefa-B/MyProject/assets/151809027/ae551c4c-c515-4625-ad29-9d274983c5b2">


**Step 2: use ssh for a secure connection**
<img width="882" alt="project_step2" src="https://github.com/Latefa-B/MyProject/assets/151809027/3f8a53e4-82e5-4fbd-b877-7e8a92a5da03">


**Step 3: create a directory for the project and set up an SSH key pair to access the instance securely** 
<img width="788" alt="project_step3" src="https://github.com/Latefa-B/MyProject/assets/151809027/85719113-3a85-457f-8123-a26512d0223c">


**Steps 4, 5 and 6 : configure ansible playbook to use the SSH key for authentication . Add the public key to authorized_keys file to establish the ssh connection**

<img width="1377" alt="project_step4" src="https://github.com/Latefa-B/MyProject/assets/151809027/34424705-666b-4ceb-806d-76decb791eab">


<img width="476" alt="project_step5" src="https://github.com/Latefa-B/MyProject/assets/151809027/6803040a-2b9e-4f45-94f5-3bc1a68e54e3">


<img width="1369" alt="project_step6" src="https://github.com/Latefa-B/MyProject/assets/151809027/2f5c84f8-ba4a-4f10-a8d3-c2f6d6a75860">


**Steps 7, 8, 9 and 10: create an ansible configuration file and an inventory file containing the targets ip addresses**

<img width="366" alt="project_step7" src="https://github.com/Latefa-B/MyProject/assets/151809027/70bd345f-79e6-42e1-ba4b-7aa873a86ca9">


<img width="867" alt="project_step8" src="https://github.com/Latefa-B/MyProject/assets/151809027/dee4706a-9388-42e6-8214-d92844555986">


<img width="919" alt="project_step9" src="https://github.com/Latefa-B/MyProject/assets/151809027/c43b7d08-16b6-47ef-9ecf-2bcd99f6421a">


<img width="529" alt="project_step10" src="https://github.com/Latefa-B/MyProject/assets/151809027/e24330e1-46c3-4b9d-8b3e-0d87946b002e">


**Step 11: check the connectivity with the targets nodes using ping module**
<img width="791" alt="project_step11" src="https://github.com/Latefa-B/MyProject/assets/151809027/65024f28-3e26-4d9a-a9b0-8227e6c3b04b">

**Step 12: create an ansible role for my project named “apache” using the command : ansible-galaxy init. The role is a 
hierarchical structure that organizes complex playbooks. The tree command shows the structure of the role**
<img width="507" alt="project_step12" src="https://github.com/Latefa-B/MyProject/assets/151809027/c11cfc0e-2ea6-47fe-945a-9a8c077ea7da">

**Steps 13 and 14: create a role yaml file to run the role (including all the playbooks)**

<img width="489" alt="project_step13" src="https://github.com/Latefa-B/MyProject/assets/151809027/b9ee020a-cb39-4598-a7cd-3f31134a17e3">


<img width="815" alt="project_step14" src="https://github.com/Latefa-B/MyProject/assets/151809027/4ac407b3-914c-42e2-8b31-084301a6ced7">


**Step 15: create a YAML based file where all the tasks are defined to set up and configure the service. created in apache 
role in tasks subdirectory, containing the tasks that will be executed.** the tasks involves : 

- task1: update ubuntu apt-get package manager and install apache web server software
- task2: start and enable apache service
- task3: create a bash script to create an html index file in the web server root directory, adding permissions and including the content.
- task4: run the bash script to generate and create an index HTML file.
- task 5: open ubuntu firewall on http port 80 to allow traffic. notifying to restart apache after reading the configuration.

  
<img width="793" alt="project_step15" src="https://github.com/Latefa-B/MyProject/assets/151809027/86ab7df9-c464-4c77-90d1-50d5206335e2">


**Step 16: run the playbook successfully using the command ansible-playbook role.yaml. it has set up the apache software, created an index HTML file, allowed http port80 and automate the deployment**
<img width="1079" alt="project_step16" src="https://github.com/Latefa-B/MyProject/assets/151809027/b6bb5fcf-66d9-445a-9f01-9289a648a2fb">

**Step 17: test the status of apache, checking that it is running**
<img width="755" alt="project_step17" src="https://github.com/Latefa-B/MyProject/assets/151809027/26ff7ea5-701a-415c-8fb3-583e45ca3eab">

**Step 18: allowing http port 80 on my AWS EC2 instances**
<img width="1356" alt="project_step18" src="https://github.com/Latefa-B/MyProject/assets/151809027/96437c10-e44d-4549-a4d5-6228cec07366">

**Step 19: while testing the access to the web page, an error message occurred : “the server where this page is located is not responding”. the reason is i have used the private IP instead of the Public IP to access the web page**
<img width="827" alt="project_step19" src="https://github.com/Latefa-B/MyProject/assets/151809027/1b33015e-e8c7-4e19-9380-b8bdb9c956c4">

**Steps 20 and 21: after testing accessing the web page with the public IP address, the access was done successfully**

<img width="835" alt="project_step20" src="https://github.com/Latefa-B/MyProject/assets/151809027/d121c00f-aca3-45e6-afc8-3b7134654f68">


<img width="1012" alt="project_step21" src="https://github.com/Latefa-B/MyProject/assets/151809027/4e09b95f-fb33-43fa-8647-8515d0425f7d">


