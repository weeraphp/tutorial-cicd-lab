# Create Service Principle Support SDK


## Prerequisites

- Install [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/) or Via Cloud Shell

## Login

if you use Azure CLI must be login before

```bash
az login
```

## Set Subscription 

you can see subscription id on https://portal.azure.com

```bash
az account set --subscription xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```

## Create Service Principle

please check and make sure subscription to create service principle then run follow command below

```bash
az ad sp create-for-rbac --name sp-[name]-tutorial --skip-assignment --sdk-auth
```

will return like this format

```json
{
  "clientId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
  "clientSecret": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
  "subscriptionId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
  "tenantId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
  "activeDirectoryEndpointUrl": "https://login.microsoftonline.com",
  "resourceManagerEndpointUrl": "https://management.azure.com/",
  "activeDirectoryGraphResourceId": "https://graph.windows.net/",
  "sqlManagementEndpointUrl": "https://management.core.windows.net:8443/",
  "galleryEndpointUrl": "https://gallery.azure.com/",
  "managementEndpointUrl": "https://management.core.windows.net/"
}
```

copy and focus at 4 key in json format then and save

!! attention !! this is a Secret please keep it private and don't share

```json
{"clientId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
  "clientSecret": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
  "subscriptionId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
  "tenantId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"}
```
