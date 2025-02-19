# git-ARM-Template

- This repository contains an ARM template to deploy a **Windows Server 2019 Datacenter** Virtual Machine in Azure, along with a template of Network Security Group (NSG) Configuration.

## Features

- **Fully automated deployment** using ARM templates.
- Creates a **Windows VM** with a customizable size.
- Configures **Virtual Network (VNet)** and Network Security Group (using ARM template to deploy) to allow RDP access.

## Files in this Repository

The files are uploaded in the repository to downlaod and perform the task.

- `template.json` --> Defines the Windows VM deployment.
- `nsg-template.json` --> Defines the Network Security Group (NSG) rules.

## How to Use

1. Ensure you are connected to Azure CLI by going to the Azure Portal or logging in through your temrinal to the Azure Account.
2. Deploy the **Windows VM** using `template.json`.
3. Command to deploy is:
```bash
az deployment group create --resource-group RG-name --template-file template.json --parameters vmName=MyWinVM adminUsername=AdminUser adminPassword="YourSecureP@ssword" subnetName=YourSubnetName
```
4. Find out the Public IP of the VM and copy it to the `nsg-template.json` file.
5. Deploy the **NSG** using the `nsg-template.json`.
6. Command to deploy is:
```bash
az deployment group create --resource-group RG-name --template-file nsg-template.json --parameters sourceIP=YOUR_PUBLIC_IP/32
```
7. Downlaod the RDP file and connect to it using proper credentials.