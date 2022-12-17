```
az storage container list --account-key ACCESS_KEY --account-name ACCOUNT_NAME
```

```
az login 
TENTANT_ID=<your-tenant-id>
```

```
az account list -o table
```

```
SUBSCRIPTION=<id>
```

```
az account set --subscription $SUBSCRIPTION
```

```
az logout
az cache purge
az account clear
```

## AKS 

```
az aks show -g aksresourcegroup -n myakscluster \
  --query addonProfiles.httpApplicationRouting.config.HTTPApplicationRoutingZoneName -o table
```

## Sign in with a service principal

```
TENANT=<tenant>
APP_ID=<id>
SECRET=<secret>
```
```
az login --service-principal -u $APP_ID -p $SECRET --tenant $TENANT
```



### Create Service Principal

```

SERVICE_PRINCIPAL_JSON=$(az ad sp create-for-rbac --skip-assignment --name aks-getting-started-sp -o json)

#Keep the `appId` and `password` for later use!

SERVICE_PRINCIPAL=$(echo $SERVICE_PRINCIPAL_JSON | jq -r '.appId')
SERVICE_PRINCIPAL_SECRET=$(echo $SERVICE_PRINCIPAL_JSON | jq -r '.password')

#grant contributor role over the resource group to our service principal

az role assignment create --assignee $SERVICE_PRINCIPAL \
--scope "/subscriptions/$SUBSCRIPTION/resourceGroups/$RESOURCEGROUP" \
--role Contributor

```

```
az ad sp create-for-rbac --name "sp-testing" --role contributor \
                          --sdk-auth
```

```
az ad sp create-for-rbac --name "sp-testing" --role contributor \
                          --scopes /subscriptions/{subscription-id}/resourceGroups/{resource-group} \
                          --sdk-auth

```

