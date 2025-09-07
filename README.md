Labb 2 – Azure-infrastruktur med Bicep
--------------------------------------

Syfte
=> Bygga en liten men realistisk molninfrastruktur i Azure med (Bicep), uppdelad i tre miljöer: dev, test och prod.


DEPLOYMENT
----------

az login
az account set --subscription "<DIN_SUBSCRIPTION>"

DEV
----
az deployment group create `
  --name dev-deployment `
  --resource-group rg-tamaraali-dev `
  --template-file ./src/main.bicep `
  --parameters ./parameters/dev.json

  PROD
  ----
  az deployment group create `
  --name prod-deployment `
  --resource-group rg-tamaraali-prod `
  --template-file ./src/main.bicep `
  --parameters ./parameters/prod.json

TEST
----
az deployment group create `
  --name test-deployment `
  --resource-group rg-tamaraali-test `
  --template-file ./src/main.bicep `
  --parameters ./parameters/test.json


Outputs URL
-----------
adminmolnlabb2-test.azurewebsites.net

adminmolnlabb2-dev.azurewebsites.net

adminmolnlabb2-prod.azurewebsites.net

Kommandon för outputs
---------------------
az deployment group show 
  --resource-group rg-<dittnamn>-dev 
  --name dev-deployment 
  --query properties.outputs
