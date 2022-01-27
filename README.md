# Edge Cluster Multi-Layer Setup using Bash Scripts  

### Abstract
The purpose of this document is to **automate setup of Cloud core and Edge core** , and install kubernetes, GoLang, and so on **using bash scripts**. Running Cloud core and Edge core and deployed mission and task to Edge node. Improve the Edge computing. This Cloud and Edge design is derived from cloud end to edge end for Edge System Functional Description and the Setup Requirements Specification. The intended user of this program is the edge computing user.


### Virtual Machine Configuration 
•	Ubuntu 18.04, one for cloud-core, two for edge-core.   
•	Open the port of 10000 and 10002 in the security group of the cloud-core machine and edge-core machine   
•	16 GB RAM, 16 vCPUs, 128 GB storage.    

### Machine 1: Cloud Core Node 
### Machine 2: Edge Node with Control Plane 
### Machine 3: Edge Worker Node

## Do the following in all the three machines:
    sudo -i
    
### Edit the sshd file to permit copy files within the Machines.
    vi /etc/ssh/sshd_config
    
### Remove comment '#' and modify the line 'PermitRootLogin yes' at line 32 and also modify line 56 to 'PasswordAuthentication yes' by removing comment.

   ![image](https://user-images.githubusercontent.com/95343388/151365629-77bf68bf-fce2-4303-8e7e-4fd68c0a7d0e.png)
   
### Now reload the sshd service
     systemctl reload sshd.service
### Now set the root password for all the machines
     passwd root
     
   ![image](https://user-images.githubusercontent.com/95343388/151366134-be0a5fa0-9800-4d5c-981b-45c3fcf8b902.png)

### 3. Run the Scripts:
       sudo bash cloud-core.sh (for machine-1)
       sudo bash edge-node-control-plane.sh (for machine 2)  (run the script only after successfully running the machine-1 script)
       sudo bash worker-node.sh (for machine 3)  (run the script only after successfully running the machine-2 script)

### 2. Input the IP's of Machine 1, Machine 2 and Machine 3  
       
   ![image](https://user-images.githubusercontent.com/95343388/151364344-0f45fa11-7ffe-414b-a2b4-2740d64b881d.png)

### 4. Verify the Edgecluster in 'Cloud Core Node' (Node-A):
       kubectl get edgecluster
       
### 5. To see Cloudcore & Edgecore logs:
       cd $HOME/go/src/github.com/fornax
       cat cloudcore.logs
       cat edgecore.logs
