# provision a DB2 database

article: https://medium.com/cooking-with-azure/deploying-db2-in-azure-on-rhel-727cfcb22a1

arm temmplate: https://github.com/ms-cse/azure-quickstart-templates/tree/101-db2-rhel-raid10/101-db2-rhel-raid10


## docker 

https://www.ibm.com/docs/en/db2/11.5?topic=system-windows

or

https://www.ibm.com/support/producthub/db2/docs/content/SSEPGG_11.5.0/com.ibm.db2.luw.db2u_openshift.doc/doc/t_install_db2CE_win_img.html


https://datageek.blog/en/2021/07/22/how-to-use-docker-on-your-local-machine-for-dbas/

````
docker run -itd --name mydb23 --privileged=true -p 50000:50000 -e LICENSE=accept -e DB2INST1_PASSWORD=pass@word1 -e DBNAME=testdb -v /c/docker/db2:/database ibmcom/db2

docker logs -f mydb23

docker exec -ti mydb23 bash -c "su - db2inst1"
````




## via CLI

`docker run -it mcr.microsoft.com/azure-cli`

`az group create -l northcentralus -n db2`

-- create a network security group

````
az network nsg create -g db2 -n db2
az network nsg rule create --nsg-name db2 -g db2 --name allow-db2 --description "DB2" --protocol tcp --priority 100 --destination-port-range "50000"
az network nsg rule create --nsg-name db2 -g db2 --name allow-ssh --description "DB2" --protocol tcp --priority 101 --destination-port-range "22"
````

create the VM

`az vm create --resource-group db2 --name db2 --image RedHat:RHEL:7-RAW-CI:latest --size Standard_DS2_v2 --admin-username rhel --data-disk-sizes-gb 10 10 10 10 --nsg db2  --no-wait`

create with custom script

````
az vm create --resource-group db2 \
--name db2 --image RedHat:RHEL:7-RAW-CI:latest \
--size Standard_DS2_v2 --admin-username rhel \
--data-disk-sizes-gb 10 10 10 10 --nsg db2 \
--custom-data ./db2_setup.sh --no-wait
````
