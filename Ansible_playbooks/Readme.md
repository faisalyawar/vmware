## Ansible playbooks for commissioning and Decommissiong the virtual machine

This readme explains about the input variables for create and delete the VM's.

##### Input variables for commissioning the virtual machine
 
- Inputs variables to be used in the commissioning the virtual machine

```
# Mandatory 
vcenter_hostname: "" # Vcenter ip address or vcenter hostname
folder: ""  # Path of the vm folder to be created
vm_name: "" # Virtual machine name
guest_id: "" # Guest id like other64guest, etc.,
disk_size_gb: "" # Disk size of virtual machine in GB
disk_type: ""  # Disk type of virtual machine like thin, thick
disk_datastore: "" # datastore name
hardware_memory_mb: "" # Hardware memory in MB -- Convert GB to MB like 1GB*1024=1024, 2GB*1024=2046
hardware_num_cpus: ""  # No of cpu's
hardware_scsi: ""  # Hardware scsi like paravirtual
network_name: "" # Network name 
network_mac: "" # If you have network mac address pass it or else make it commented
network_ip: ""  # If you have network ip address pass it or else make it commented
network_netmask: ""  # If you have network netmask pass it or else make it commented
network_device_type: "" Network device type is like vmxnet3
# Optional variables
wait_for_ip_address: ""
wait_for_ip_address_timeout: ""
validate_certs: ""  # If you have valid certificate pass with true boolean value
```


##### Input variables for decommissioning the virtual machine
 
- Inputs variables to be used in the decommissioning the virtual machine

```
# Mandatory 
vcenter_hostname: "" # Vcenter ip address or vcenter hostname
folder: ""  # Path of the vm folder to be created
vm_name: "" # Virtual machine name
# Optional variables
validate_certs: ""  # If you have valid certificate pass with true boolean value
```
