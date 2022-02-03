# Edge Cluster Multi-Layer Setup using Bash Scripts  



### Virtual Machine Configuration 



•	**3 Ubuntu 18.04 VMs, one for cloud-core, two for edge-core.**   
•	Open the port of 10000 and 10002 in the security group of the cloud-core machine and edge-core machine   
•	16 GB RAM, 16 vCPUs, 128 GB storage.    

####     Machine 1: Cloud Core Node 
####     Machine 2: Edge Node with Control Plane 
####     Machine 3: Edge Worker Node

## Do the following steps in all the three machines for smoothly running the bash scripts:




#### 1) Switch to root user:
     sudo -i
    
#### 2) Edit the sshd file to permit copy files within the Machines:

     vi /etc/ssh/sshd_config
    
#### 3) Remove comment '#' and modify the line 'PermitRootLogin yes' at line 32 and also modify line 56 to 'PasswordAuthentication yes' by removing comment in 'sshd_config' file:

   ![image](https://user-images.githubusercontent.com/95343388/152106709-a9370a4d-8d82-4d66-8780-3a5e18fc0275.png)
   
#### 4) Now reload the sshd service:

      systemctl reload sshd.service
     
#### 5) Now set the root password for all the machines:

      passwd root
 
   ![image](https://user-images.githubusercontent.com/95343388/152161347-604d1b3a-3f27-44fe-9fef-8a3b2f8248bc.png)

   
### NOTE: 'prerequisite_package.sh' contains all the required packages for creating Kubernetes Cluster.
   
#### 6) Run the Scripts:
       sudo bash cloudcore_node.sh                  (Run in machine-1)
       sudo bash edgecore_control_plane.sh          (Run in machine 2)  (run the script only after successfully running the machine-1 script)
       sudo bash edge_worker_node.sh                (Run in machine 3)  (run the script only after successfully running the machine-2 script)

#### 7) Input the Private IP's and Password of Machine 1, Machine 2 and Machine 3:
       
   ![image](https://user-images.githubusercontent.com/95343388/152158030-2d2a26e9-71e9-4abd-8f04-0330424a32f6.png)

#### 8) Verify the Edge cluster by running command in 'Cloud Core Node' (Machine-1):

       kubectl get edgecluster
       
  ![image](https://user-images.githubusercontent.com/95343388/152162045-d6143680-14eb-470c-89c6-6f4a21e54414.png)

           
#### 9) To see Cloudcore & Edgecore logs:

       cd $HOME/go/src/github.com/fornax
       cat cloudcore.logs
       cat edgecore.logs
