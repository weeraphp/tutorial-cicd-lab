# Create App Service (for Container)

<img src="../images/82.png" alt="drawing" width="200"/>

- Go to Create Resouce

<img src="../images/3.png" alt="drawing" width="500"/>

- Select Resouce for create (Web App)
- Create Web App
  - Detail
    - Resource Group : rg-[name]-tutorial-001
    - Name : app-[name]-tutorial-backend-dev-001
    - Publish : Docker Container
  - App Service Plan (New) : Default
  - Docker
    - Options : Single Container
    - Image Source : Azure Container Registry
    - Registry : acr[name]tutorial001
    - Image : [name]-tutorial-[?]end
    - Tag : ondev ```0.0.1-SNAPSHOT``` / tag 1.0.0
  - Review + create

Create

<img src="../images/83.png" alt="drawing" width="500"/>

Select first image

<img src="../images/110.png" alt="drawing" width="500"/>

Deployment 

<img src="../images/84.png" alt="drawing" width="500"/>

Overview 

<img src="../images/85.png" alt="drawing" width="500"/>

Try to Browse

<img src="../images/86.png" alt="drawing" width="500"/>