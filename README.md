# AzureDynamicInventory


Based of this:
https://faun.pub/lets-do-devops-dynamic-host-inventories-in-azure-on-ansible-awx-tower-87437f2838c1



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
