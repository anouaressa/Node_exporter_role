# Ansibel role for anstaling node exporte 

## Set up Ansible:  

Make sure you have Ansible installed on the machine from which you'll run the playbook. 

# reate an Ansible Inventory:

Create an Ansible inventory file (e.g., inventory.ini). The inventory file defines the hosts on which you want to install Node Exporter. For each host, specify the SSH user and IP address. If you have 

multiple hosts, list them under different groups.

[nodes]
your_target_host ansible_ssh_user=your_ssh_user ansible_ssh_host=your_target_ip

# clone the role 

# write a simple playbook and use the role

---
- name: Install Prometheus Node Exporter
  hosts: nodes
  become: yes
  roles:
    - Node_exporter_role

# The steps for instaling node exporte:

# Node exporter : installation binaire


 1 Download Node Exporter binary from the specified URL.  
 
 2 Extract the downloaded binary to /usr/local/bin.  
 
 3 Create a system user called node_exporter with the /bin/false shell.  
 
 4 Set ownership of the Node Exporter binary to the node_exporter user and group.  
 
 5 Copy the systemd service template to the /etc/systemd/system directory.  
 
 6 Notify the systemd handler to reload systemd configuration after copying the service file.  
 
 7 Enable and start the Node Exporter systemd service.  

