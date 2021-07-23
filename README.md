# AzureDynamicInventory


Based on this:
https://faun.pub/lets-do-devops-dynamic-host-inventories-in-azure-on-ansible-awx-tower-87437f2838c1


1. Add credentials
2. Create a project with this repo as the git source
3. Create an inventory that references the credential, project, and inventories/azure/all_running_hosts.azure_rm.yml
3a. Add these environment variables to the inventory variables:
AZURE_SUBSCRIPTION_ID: "{{AZURE_SUBSCRIPTION_ID}}"
AZURE_CLIENT_ID: "{{AZURE_CLIENT_ID}}"
AZURE_SECRET: "{{AZURE_SECRET}}"
AZURE_TENANT: "{{AZURE_TENANT}}"

Projects
Hit sync button next to project name to pull down any changes from git

Inventories
Select Inventory Name
Select Sources
Hit sync button next to source

Templates
Create template that references the AWX/Tower project, inventory, playbook, and credentials.
Use LIMIT like you would with --limit to specify the host(s), group(s) to run against
Use JOP TYPE to specify --check, run, scan

To Do:
Haven't figured out how to get it to pull in stopped (deallocated) VMs. Tried removing below from the inventory playbook but it still skips them.

exclude_host_filters:
- powerstate != 'running'
