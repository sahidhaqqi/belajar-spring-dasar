# Belajar Spring Dasar

by Programmer Zaman Now

# Trigger jenkins

#step 1
export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
export PATH=$JAVA_HOME/bin:$PATH

java -version
mvn -version

mvn clean install

#step 2
./mvnw compile test-compile

#step 3
./mvnw test



apt update
apt install openjdk-11-jdk-headless -y

wget https://get.jenkins.io/war-stable/latest/jenkins.war


 cat /root/.jenkins/secrets/initialAdminPassword

6d8cdfe48f07424a9f87532c0504af12


root@jenkins:~# java -jar jenkins.war --httpPort=9090 &


# buat matiin
fuser -k 9090/tcp




root@jenkins:~# sudo useradd -m -d /var/lib/jenkins -s /bin/bash jenkins
root@jenkins:~# sudo mkdir -p /var/lib/jenkins
sudo cp /root/jenkins.war /var/lib/jenkins/
sudo cp -r /root/.jenkins /var/lib/jenkins/
root@jenkins:~# sudo chown -R jenkins:jenkins /var/lib/jenkins
root@jenkins:~# sudo nano /etc/systemd/system/jenkins.service

[Unit]
Description=Jenkins Servera
After=network.target

[Service]
Type=simple
User=jenkins
WorkingDirectory=/var/lib/jenkins
Environment="JENKINS_HOME=/var/lib/jenkins/.jenkins"
ExecStart=/usr/bin/java -jar /var/lib/jenkins/jenkins.war --httpPort=9090
Restart=always

[Install]
WantedBy=multi-user.target


root@jenkins:~# sudo systemctl daemon-reload
sudo systemctl restart jenkins
root@jenkins:~# systemctl status jenkins





mkdir -p /var/lib/jenkins/.ssh
ssh-keyscan -t ed25519 github.com >> /var/lib/jenkins/.ssh/known_hosts
chown -R jenkins:jenkins /var/lib/jenkins/.ssh
chmod 700 /var/lib/jenkins/.ssh
chmod 644 /var/lib/jenkins/.ssh/known_hosts






yang bakal dipakai untuk slacks
Team Subdomain: workspace-gem6945
