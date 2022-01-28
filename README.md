# Edge Cluster Multi-Layer Setup using Bash Scripts  



### Abstract


The purpose of this document is to **automate setup of Cloud core and Edge core** , and install kubernetes, GoLang, and so on **using bash scripts**. Running Cloud core and Edge core and deployed mission and task to Edge node. Improve the Edge computing. This Cloud and Edge design is derived from cloud end to edge end for Edge System Functional Description and the Setup Requirements Specification. The intended user of this program is the edge computing user.


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

   ![image](https://user-images.githubusercontent.com/95343388/151365629-77bf68bf-fce2-4303-8e7e-4fd68c0a7d0e.png)
   
#### 4) Now reload the sshd service:
      systemctl reload sshd.service
     
#### 5) Now set the similar root password for all the machines:
      passwd root
 
   ![image](https://user-images.githubusercontent.com/95343388/151366134-be0a5fa0-9800-4d5c-981b-45c3fcf8b902.png)
   
   
#### 6) Run the Scripts:
       sudo bash cloud-core.sh                 (Run in machine-1)
       sudo bash edge-node-control-plane.sh    (Run in machine 2)  (run the script only after successfully running the machine-1 script)
       sudo bash worker-node.sh                (Run in machine 3)  (run the script only after successfully running the machine-2 script)

#### 7) Input the Private IP's of Machine 1, Machine 2 and Machine 3:
       
   ![image](https://user-images.githubusercontent.com/95343388/151502797-444c6570-8efe-45f4-9e0f-f8479c6c4a20.png)

#### 8) Verify the Edge cluster in 'Cloud Core Node' (Machine-1):
       kubectl get edgecluster
       
  ![image](https://user-images.githubusercontent.com/95343388/151367806-e28dd3be-3cdd-4211-95b8-c3085dedc5c6.png)

           
#### 9) To see Cloudcore & Edgecore logs:
       cd $HOME/go/src/github.com/fornax
       cat cloudcore.logs
       cat edgecore.logs
