# Overview

A quick and dirty way to host the Pihole DNS service on Azure Container Instances 

# Deploy External Facing Pihole
```
cd infrastructure 
az group create --name Pihole_RG --location southcentralus
az deployment group create --name external --resource-group Pihole_RG --template-file=azuredeploy.external.json --parameters @azuredeploy.parameters.json
```

# Deploy Internal Facing Pihole
```
cd infrastructure 
az group create --name Pihole_RG --location southcentralus
az deployment group create --name internal --resource-group Pihole_RG --template-file=azuredeploy.internal.json --parameters @azuredeploy.parameters.json
```

#Note:
* Requires an existing Azure virtual network with a subnet named DNS
* After pihole is created, the Azure virtual network DNS configuration will need to be updated to the pihole's IP address