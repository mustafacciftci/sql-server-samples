
# Deploy a SQL Server big data cluster on Azure Kubernetes Service (AKS) 

Using this sample Python script, you will deploy a Kubernetes cluster in Azure using AKS and a SQL Server big data cluster using this AKS cluster as its environment. The script can be run from any client OS.


## Pre-requisites

1. Running the script will require: [python minimum version 3.0](https://www.python.org/downloads)
1. Ensure you have installed `mssqlctl` CLI and its prerequisites:
    - Install [pip3](https://pip.pypa.io/en/stable/installing/).
    - Install/update requests package. Run the command below using elevated priviledges (sudo or admin cmd window):
        ```
        python -m pip install requests
        python -m pip install requests --upgrade
        ```
    - Install mssqlctl CLI latest version using . Run the command below using elevated priviledges (sudo or admin cmd window):
        ```
        pip3 install --index-url https://private-repo.microsoft.com/python/ctp-2.0 mssqlctl
        ```
1. Login into your Azure account. Run this command:
```
az login
```

## Instructions

Run the script using:
```
python deploy-sql-big-data-aks.py
```

>[!Note]
>
>If you have both pyhon3 and pyhon2 on your client machine and in the path, you will have to run the command using pyhon3:
>```
>python3 deploy-sql-big-data-aks.py
>```


When prompted, provide your input for Azure subscription ID, Azure resource group to create the resources in, and Docker credentials. Optionally, you can also provide your input for below configurations or use the defaults provided:
- azure_region
- vm_size - we recommend to use a VM size to accommodate your workload. Default `Standard_DS3_v2` is minimum for running just basic validations
- aks_node_count - this is the number of the worker nodes for the AKS cluster, excluding master node 
- cluster_name - this value is used for both AKS cluster and SQL big data cluster created on top of AKS. Note that the name of the SQL big data cluster is going to be a Kubernetes namespace
- password - same value is going to be used for all accounts that require user password input: SQL Server master instance SA account, controller user and Knox user
- controller_username - this is the username for the cluster admin account