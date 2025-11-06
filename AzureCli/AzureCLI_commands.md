1) How to connect Azure CLI with GitBash
   - Install Git for Windows: This includes Git Bash.
   - Install the Azure CLI on Windows: Download and run the Microsoft Installer (MSI) for the Azure CLI. 
   This installer typically adds the az command to your Windows system's PATH environment variable automatically.
   Verify the installation: After installation, close and reopen your Git Bash terminal, 
   then run:az version
   
2) Log in to Azure (a browser window will open for authentication)
    az login
	Select subscription
	
3)  create resource group
    az group create --name mytest --location eastus (mytest=resourcegroup name , eastus=location
	
4) command to check list of resourcegroup
   az group list
   
5) Delete resourcegroup
   az group delete --name Resourcegp (Resourcegp is resource groupname)
   
6) Deploy VM in azure
   az vm create \
  --resource-group testrg1 \  #testrg1 is resource-group
  --name vm1 \
  --image Ubuntu2204 \
  --size Standard_B1s \
  --admin-username azureuser \
  --generate-ssh-keys \
  --zone 3 \
  --public-ip-sku Standard
  
7) connect vm 

  ssh username@publicip
  
8) shutdown vm from azure cli
  az vm stop --resource-group testrg1 --name vm1
  
9) Start VM from shutdown state
  az vm start --resource-group --name vm1
  
10) stop and deallocate VM
  az vm deallocate --resource-group testrg1 --name vm1

11) delete azure vm
   az vm delete --resource-group --name vm1
   
12) command to find publlic ip associated with my VM
   az vm list-ip-addresses  #it will list all public ip-addresses

13) command to ffind public ip address of perticular VM
   az vm show -d --resource-group mygrp1 --name vm1 --query 'publicIps'
   
14) Quick command to open specific port (e.g 8080) inbound for vm
   az vm open-port --port 8080 --resource-group myrg1 --name vm1 
   
15) delete specific port from NSG 
  az network nsg rule delete --resource-group myrg1 --nsg-name vm1NSG --name open-port-8080  #open-port-8080 is inboud rule
  
16) command to retrive list of rules from NSG 
  az network nsg rule list --resource-group myrg1 --nsg-name vm1NSG
  