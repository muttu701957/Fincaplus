Create a ubuntu machine 
sudo su
chmod 777 jenkins.sh
ls
./jenkins.sh
 apt install docker.io -y
 service docker start
sudo usermod -aG docker $USER
service jenkins restart
 sudo usermod -aG docker jenkins
 service jenkins restart





