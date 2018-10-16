## Organisation Web hosting Virtualmin Ansible roles

<!-- # These ansible project contains various roles that install and configures an optimized and secure web hosting environment using virtualmin
 -->
- Applications installed

	- Virtualmin
	- iptables
	- config server firewall (csf)
	- modsecurity
	- maldet
	- rkhunter

# mandatory variables

<!-- 	iptables default variables
 --><!-- 	update file: /iptables/default/main.yml -->

		Institution_prefix: "XXX.XX.XX.0/24" ## Replace this ip with institution/organisation browsing prefix

<!-- - populate the ssh listen on address and port (CSF) role && enable csf parameter.
- file: /csf/defaults/main.yml
 -->
		---
		testing: 0
		csf_sec_ssh_port: 22
		Listen_address: XX.XX.XX.XX # VM IP address for ssh listen on address
		Institution_prefix: "XX.XX.XX.0/24" ## Replace this ip with institution browsing prefix



<!-- Maldet email -->

# Specify the email address to send scan reports to

your_email: "username@domain"


<!-- rkhunter email
 -->
<!-- # Email a message to this address if a warning is found when the system is
# being checked. Multiple addresses may be specified simply be separating
# them with a space. -->

rkhunter_warning_mail_address: "username@domain"

<!-- Configure VM for ssh using public keys
 -->
# Generate ans copy ssh keys
 ssh-keygen ## generate public keys
 ssh-copy-id -i ~/.ssh/id_rsa.pub root@remote_ip 
<!-- Edit the inventory file and update the Installation VM IP
 -->
 vi inventory.txt

 cat inventory.txt 

[virtualmin_instance]
XX.XX.XX.XX
# <!-- Run the Ansible main playbook  -->
 ansible-playbook virtualmin.yaml -i inventory.txt
