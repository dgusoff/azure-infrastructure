
# Cosmos DB

## create via CLI

open shell

`docker run -it mcr.microsoft.com/azure-cli`

log in - service principal

`az login --service-principal -u <app-id> -p <password-or-cert> --tenant <tenant>`
  
log in - interactive

`az login`

list resource groups

`az group list --output table`

create a resource group

`az group create -l northcentralus -n cosmos`

create a cosmosdb account


tbd

create a cosmos DB Mongo instance

`az cosmosdb mongodb database create --account-name mongo-account  --name my-cosmos --resource-group cosmos`
