# Create Kubernetes Service

<img src="../images/5.png" alt="drawing" width="200"/>

- Go to Create Resouce

<img src="../images/3.png" alt="drawing" width="500"/>

- Find resource then select Kubernetes Service
- Create Kubernetes cluster
  - Basic
    - Project details
      - Resource Group : rg-[name]-tutorial-001
      - Cluster details
        - Kubernetes cluster name
   : aks-[name]-tutorial-001
        - Location : South
      - Node pools
        - agentpool
      - Authenication
        - Cluster infrastructure
          - Authentication method : Service principal [create service principle](create-sp.md)
          - Service principal client ID : xxxxxxxxxxx
          - Service principal client secret : xxxxxxxxxx
        - Networking
          - Network configuration: Kubenet
          - DNS name prefix : aks-[name]-tutorial-001-dns
          - Traffic routing
            - Enable HTTP application routing : Enable (when debug dns)
        - Integrations
          - Container monitoring : Disabled
  - Review + create

Create

<img src="../images/11.png" alt="drawing" width="500"/>


Deployment 

<img src="../images/13.png" alt="drawing" width="500"/>

Overview 

<img src="../images/14.png" alt="drawing" width="500"/>
