# Kasm Workspace Deployment Using Docker Swarm 
**Task Details: ** 

Create 3 virtual machines in VirtualBox using Vagrant. Deploy Kasm Workspace using Docker Swarm for multiple users.  

**Perquisites:** Vagrant, VirtualBox, ubuntu/focal64 box 

You can box using following command 

**Run:** vagrant box add ubuntu/focal64 

**Step1:** Create 3 virtual machines, (Master, Slave1, Slave2) Using Vagrant  

**Step2:** Run the following command from the same directory where vagrantfile is located. 

**Run:** vagrant up 

Now you have 3 VMs up and running  

**Step 3:** ssh into all the virtual machines using following command  

**Run:** vagrant ssh vm-name (eg. Vagrant ssh master) 

**Step4:** Install docker on all virtual machines 

**Step5:** Now on master Vm run the Following command on it so it behave as master/Leader node in Swarm Cluster 

**Run:** docker swarm init –advertise-addr private-ip 

**Step6:** Run the following command on all slave node so they can join the swarm cluster as worker nodes 

**Run:** docker swarm join –token <token> master-node-ap worker 
 
 **Step7:** Verify using following command 
**Run:** docker node ls 

**Step8:** Download the docker-compose.yml file

**Step9:** Now Run following commands from the same directory where docker-compose.yml file exists 

**Run:** docker stack deploy -c docker-compose.yml kasm  

**Step10:** Verify the setup by running following commands 

**Run:** docker stack ls 

**Run:** docker services ls

**Step11:** Verify in browser 

https://vm-ip:6901 


