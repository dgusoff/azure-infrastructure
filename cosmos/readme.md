
# Cosmos DB

## create via CLI

[docs](https://docs.microsoft.com/en-us/cli/azure/cosmosdb?view=azure-cli-latest)

[mongoDB docs](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb/mongodb-introduction)

[node quickstart](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb/create-mongodb-nodejs#sign-in-to-azure)

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

check if a cosmos db account exists

`az cosmosdb check-name-exists --name MyCosmosDBDatabaseAccount`


create a cosmos DB account

`az cosmosdb create --name MyCosmosDBDatabaseAccount --resource-group cosmos --subscription MySubscription`

delete an azure cosmos db account

`az cosmosdb delete --name MyCosmosDBDatabaseAccount --resource-group cosmos`

create a cosmos DB Mongo instance

`az cosmosdb mongodb database create --account-name mongo-account  --name my-cosmos --resource-group cosmos`


## create mongo cosmosDB - walkthrough

`az group create -l northcentralus -n cosmos`

create the account(account name must be globally unique)

`az cosmosdb create --name mongo-account --resource-group cosmos --kind MongoDB`


