# Edge Cluster Multi-Layer Setup using Bash Scripts  

### Abstract
The purpose of this document is to **AUTOMATE setup of Cloud core and Edge core** , and describe the each step to create virtual machine setup the port number, install kubernetes, GoLang, and so on **USING BASH SCRIPTS**. Running Cloud core and Edge core and deployed mission and task to Edge node. Improve the Edge computing. This Cloud and Edge design is derived from cloud end to edge end for Edge System Functional Description and the Setup Requirements Specification. The intended user of this program is the edge computing user.


### Virtual Machine Configuration 
•	Ubuntu 18.04, one for cloud-core, two for edge-core.   
•	Open the port of 10000 and 10002 in the security group of the cloud-core machine and edge-core machine   
•	16 GB RAM, 16 vCPUs, 128 GB storage.    

### Node-A: Cloud Core Node 
### Node-B: Edge Node with Control Plane 
### Node-C: Edge Worker Node

### 2. Input the IP's in 'cloud-core.sh ' & 'edge-node-control-plane.sh':
       

### 3. Run the Scripts:
       sudo bash cloud-core.sh (for node-a)
       sudo bash edge-node-control-plane.sh (for node-b)  (run the script only after successfully running the node-a script)
       sudo bash worker-node.sh (for node-c)  (run the script only after successfully running the node-b script)
  
### 4. Verify the Edgecluster in 'Cloud Core Node' (Node-A):
       kubectl get edgecluster
       
### 5. To see Cloudcore & Edgecore logs:
       cd $HOME/go/src/github.com/fornax
       cat cloudcore.logs
       cat edgecore.logs
