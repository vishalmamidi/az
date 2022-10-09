# az

```
az login 
TENTANT_ID=<your-tenant-id>
```

## view and select your subscription account

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
