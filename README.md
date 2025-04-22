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
 
 service jenkins restart\
 
add all plugins like docker, kubernetes, trivy
 
add credentials of docker.hub, kubernetes, github on jenkins


setup kubernetes cluster using kubeadm( 1 master and 1 node machine)

write yaml files related to pods, deployment, service, hpa

create pipeline and write pipelinescript and stages and execute all stages

stages include maven build, dokcer, kubernetes, trivy

automated and addedd github webhook to automatically build in jenkin pipeline if any changes

successfully executed the whole pipeline and performed end to end automation



![1](https://github.com/user-attachments/assets/f779c11b-b3e2-45a4-bdc9-50998e2e03f7)
![2](https://github.com/user-attachments/assets/07f9fc44-b3fe-4989-9e39-c032f7437594)
![3](https://github.com/user-attachments/assets/0bba5571-19c7-4fd7-a1c3-083378f485df)
![4](https://github.com/user-attachments/assets/9bb4d24e-3cc5-4b40-8e44-6fdf38d07aef)
![5](https://github.com/user-attachments/assets/a69f485a-00cc-4d43-887a-9c2eea827c52)
![6](https://github.com/user-attachments/assets/210c200a-2b45-4ad6-ae0e-c459c8835b6d)
![7](https://github.com/user-attachments/assets/eb3b93b9-5fd5-4dde-a7e6-db86bfeadcff)
![8](https://github.com/user-attachments/assets/a69d5864-823d-4ba9-85f3-dec92c66a733)
![9](https://github.com/user-attachments/assets/95439dd5-c561-4b97-bc0b-042ee458b0f3)
![9](https://github.com/user-attachments/assets/0ad8ccfc-4033-421e-af30-f932e8f52766)
![10](https://github.com/user-attachments/assets/ea876ff5-6520-4c1a-a0af-73431361c855)
![11](https://github.com/user-attachments/assets/37b1cd10-7aef-4ca3-93c1-232dab8762ab)


















