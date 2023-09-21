# Kasm Workspace Deployment Using Docker Swarm 
# Task Details:  

Create 3 virtual machines in VirtualBox using Vagrant. Deploy Kasm Workspace using Docker Swarm for multiple users.  

Perquisites: Vagrant, VirtualBox, ubuntu/focal64 box 

You can box using following command 

Run: vagrant box add ubuntu/focal64 

# Step1: Create 3 virtual machines, (Master, Slave1, Slave2) Using Vagrant  

# Step2: Run the following command from the same directory where vagrantfile is located. 

vagrant up 

Now you have 3 VMs up and running  

# Step 3: ssh into all the virtual machines using following command  

vagrant ssh vm-name (eg. Vagrant ssh master) 

Step4: Install docker on all virtual machines 

# Step4: Now on master Vm run the Following command on it so it behave as master/Leader node in Swarm Cluster 

docker swarm init –advertise-addr private-ip 

Now  

# Step5: Run the following command on all slave node so they can join the swarm cluster as worker nodes 

docker swarm join –token <token> master-node-ap worker 
# Step6: Download the docker-compose.yml file

# Step7: Now Run following commands from the same directory where docker-compose.yml file exists 

docker stack deploy -c docker-compose.yml kasm  

# Step8: Verify the setup by running following commands 

docker stack ls 

docker services ls i 

# Step9: Verify in browser 

https://vm-ip:6901 

Verify using following command 

docker node ls 
