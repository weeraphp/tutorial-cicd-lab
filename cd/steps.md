# Steps in Jobs

## Checkout pipelines

```yaml
- name: "Checkout pipelines"
    uses: actions/checkout@v2
    with:
    path: .pipeline
```

## Checkout project

```yaml
- name: "Checkout project"
    uses: actions/checkout@v2
    with:
    repository: ${{ env.REPOSITORY }}
    ref: ${{ env.GITREF }}
    token: ${{ secrets.REPO_ACCESS_TOKEN }}
```

## List working directory

```yaml
- name: "List working directory"
  run: ls
```
## Login via Azure CLI

```yaml
- name: 'Login via Azure CLI'
  uses: azure/login@v1
  with:
  creds: ${{ secrets.AZURE_RBAC_CREDENTIALS }}
  allow-no-subscriptions: true
```

## Set subscription

```yaml
- name: 'Set subscription'
  run: az account set --subscription xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```

## Deploy to Azure Web App

```yaml
- name: "Deploy to Azure WebApp"
  uses: azure/webapps-deploy@v2
   with:
     app-name: ${{ format('app-[name]-tutorial-frontend-{0}-001', 'dev') }}
     images: '${{ env.CONTAINER_REPOSITORY }}/${{ env.APP_NAME }}:${{env.IMAGE_TAG}}'
```

## Set Web App Settings

```yaml
- name: Set Web App Settings
  uses: Azure/appservice-settings@v1
  with:
    app-name: ${{ format('app-[name]-tutorial-frontend-{0}-001', 'dev') }}
    app-settings-json: |
      [
        {
          "name": "VUE_APP_ENPOINT_API_BACKEND",
          "value": "https://app-[name]-tutorial-backend-dev-001.azurewebsites.net/api",
          "slotSetting": false
        }
      ]
```

