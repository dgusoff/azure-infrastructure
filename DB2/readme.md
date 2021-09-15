# provision a DB2 database

article: https://medium.com/cooking-with-azure/deploying-db2-in-azure-on-rhel-727cfcb22a1

arm temmplate: https://github.com/ms-cse/azure-quickstart-templates/tree/101-db2-rhel-raid10/101-db2-rhel-raid10


## via CLI

`docker run -it mcr.microsoft.com/azure-cli`

`az group create -l northcentralus -n db2`

-- create a network security group

````
az network nsg create -g db2 -n db2
az network nsg rule create --nsg-name db2 -g db2 --name allow-db2 --description "DB2" --protocol tcp --priority 100 --destination-port-range "50000"
az network nsg rule create --nsg-name db2 -g db2 --name allow-ssh --description "DB2" --protocol tcp --priority 101 --destination-port-range "22"
````


