# Steps in Jobs

## Checkout pipelines

```yaml
steps:
- name: "Checkout pipelines"
  uses: actions/checkout@v2
```

## Login via Azure CLI

```yaml
steps:
- name: 'Login via Azure CLI'
  uses: azure/login@v1
  with:
    creds: ${{ secrets.AZURE_RBAC_CREDENTIALS }}
    allow-no-subscriptions: true
```

## Set subscription

```yaml
steps:
- name: 'Set subscription'
  run: az account set --subscription xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

```

## Deploy to Azure WebApp

```yaml
steps:
- name: "Deploy to Azure WebApp"
  uses: azure/webapps-deploy@v2
  with:
    app-name: ${{ env.AZURE_WEB_APP_NAME }}
    images: '${{ env.CONTAINER_REPOSITORY }}/${{ env.APP_NAME }}:${{env.IMAGE_TAG}}'
```

## Set Web App Settings

```yaml
steps:
- name: Set Web App Settings
  uses: Azure/appservice-settings@v1
  with:
    app-name: ${{ env.AZURE_WEB_APP_NAME }}
    app-settings-json: |
      [
        {
          "name": "XXXXX",
          "value": "YYYYY",
          "slotSetting": false
        }
      ]

```