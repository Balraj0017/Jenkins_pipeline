# Jenkins_pipeline
## Step 1: Create Two EC2 Instances
1. First, you need to create two EC2 instances on AWS. One will be the master and the other will be the agent
2. Configure the security group to allow inbound traffic on port 22 (SSH), port 80 (HTTP), and port 8080 (Jenkins)
3. Repeat these steps to create another EC2 instance for the agent. Make sure you use the same key pair for both instances.
## Step 2: Connect Master with Agent using SSH Keys
1. Next, you need to establish a secure connection between the master and the agent using SSH keys. This will allow the master to authenticate and communicate with the agent without requiring a password
2. Verify that you can log in to the agent from the master without a password using ssh
## Step 3: Install Jenkins on Master and Agent
1. Update the package list using sudo apt update
2. Install Java using sudo apt install openjdk-11-jdk
3. Add the Jenkins repository key using wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
   Add the Jenkins repository URL using sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
4. Update the package list again using sudo apt update
   Install Jenkins using sudo apt install jenkins
   Start and enable Jenkins service using sudo systemctl start jenkins and sudo systemctl enable jenkins
5. Install Java on the agent
## Create an Agent on Master and Configure its Launch Method and Credentials

### To create an agent on the master and configure its launch method and credentials, follow these steps:

1. Go to Manage Jenkins > Manage Nodes and Clouds > New Node

2. Enter a name for the agent (e.g. agent) and choose Permanent Agent
   Click OK
### Enter the following configuration for the agent:
1. Remote root directory: /home/ubuntu (or any other directory that you want to use for Jenkins workspace)
2. Launch method: Launch agents via SSH
   Host: agent-ip (the public IP address of your agent instance)
3. Credentials: Add > Jenkins > SSH Username with private key > Enter username (ubuntu) and private key (paste the content of your key pair file .pem) > Add > 
   Choose the credential that you just added
## Create a Pipeline Job on Master
1. Create a freestyle project
2. Add the build step >> Execute shell
3. Copy and paste the commands
4. wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
   wget https://chromedriver.storage.googleapis.com/92.0.4515.107/chromedriver_linux64.zip
   unzip chromedriver_linux64.zip
   sudo mv chromedriver /usr/bin/chromedriver
   sudo chown root:root /usr/bin/chromedriver
   sudo chmod +x /usr/bin/chromedriver













