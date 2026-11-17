## Ansible Playbooks
### Update Order
Updates start at 9:00am in America/Los_Angeles timezone every Saturday and proceed as follows
- 9:00am
    - All VMs run OS update playbook
    - Specific VMs will run certain playbooks based on installed services to update said services
    - All pods in the Talos K8s cluster are updated
- 9:20am
    - All PVE Hosts Run OS update playbook
    - All K8s nodes are drained to prepare for host reboots
- 9:30am
    - DNS server VMs update OS and Technitium DNS
- 9:35am
    - Maintenance window takes affect for monitoring systems to account for services going down during reboots
- 9:40am
    - reboot PBS
    - PVE hosts reboot at intervals of 5 minutes (keeps redudant services available)
        - 9:40 - pm-latitude
        - 9:45 - pm-dell
        - 9:50 - pm-lenovo
- 10:00am
    - All K8s nodes are uncordoned and pods are redeployed
- 10:10am
    - Maintenance window ends, montioring systems will alert if services are not up and running properly