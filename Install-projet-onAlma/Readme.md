## Install Jenkins on Alma linux 8.9
      yum update
      yum install wget
##### put command:
      sudo wget -O /etc/yum.repos.d/jenkins.repo \
      https://pkg.jenkins.io/redhat-stable/jenkins.repo
      sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
      sudo dnf upgrade
      sudo dnf install fontconfig java-17-openjdk
      sudo dnf install jenkins
Note: jenkins must install in yum.repos.d according jenkins
### start jenkins
#### frist enable:
       sudo systemctl enable jenkins
##### Run jenkins:
      sudo systemctl start jenkins

### Note: By default il will be create a user called jenkins
now add jenkins with group wheel

      sudo usermod -aG wheel jenkins

Stop firewall by commnad line:

      sudo systemctl stop firewalld

##### Access jenkins by browser: ip_adress:8080 and put password, install plugin, define username and password(by default username:admin) info:usr : admin, password: Inaya109   


Note: Test build by Jenkins allways on client server.