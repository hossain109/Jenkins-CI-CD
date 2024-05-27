## Installation on EC2 Instance
- Go to Console
- Running instances
- Launch instance

## Install Jenkins
Pre-requisites
-Java( jdk , jre)
Install java
>sudo apt update
>sudo apt install openjdk-11-jre

#### Jenkins:
      curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
      /usr/share/keyrings/jenkins-keyring.asc > /dev/null
      echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
      https://pkg.jenkins.io/debian binary/ | sudo tee \
      /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins

**Note: ** By default, Jenkins will not be accessible to the external world due to the inbound traffic restriction by AWS. Open port 8080 in the inbound traffic rules as show below.

- EC2 > Instances > Click on
- In the bottom tabs -> Click on Security
- Security groups
- Add inbound traffic rules as shown in the image (you can just allow TCP 8080 as well, in my case, I allowed All traffic).
![inbound_images](/Images/inbound_traffic.jpg)
## Configure EC2 Inbound traffic rules and fixed port 8080 from security Group 
## Login to jenkins by url: http:// public_ip_address:8080 
## Create first Admin user and then install docker as agent
- Log in to Jenkins.
- Go to Manage Jenkins > Manage Plugins.
- In the Available tab, search for "Docker Pipeline".
- Select the plugin and click the Install button.
- Restart Jenkins after the plugin is installed.
  Note(must be restart jenkins ex:http://ipadress:8080/restart)

## Docker agent configuration
#### Run the below command to Install Docker
      sudo apt update
      sudo apt install docker.io

### Grant Jenkins user and Ubuntu user permission to docker deamon.
      sudo su - 
      usermod -aG docker jenkins
      usermod -aG docker ubuntu
      systemctl restart docker

Once you are done with the above steps, it is better to restart Jenkins.

http://<ec2-instance-public-ip>:8080/restart
The docker agent configuration is now successful.
