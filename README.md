## Ansible Playbooks
### Update Order
Updates start at 9:00am in America/Los_Angeles timezone every Saturday and proceed as follows
- 9:00am
    - All VMs run OS update playbook
    - Specific VMs will run certain playbooks based on installed services to update said services
- 9:20am
    - All PVE Hosts Run OS update playbook
- 9:30am
    - DNS server VMs update OS and DNS server
- 9:40am
    - reboot PBS
    - PVE hosts reboot at intervals of 5 minutes
        - 9:40 - pm-latitude
        - 9:45 - pm-dell
        - 9:50 - pm-lenovo
As of now, all updates should complete by 10:00am