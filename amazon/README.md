# AWS

Test deployment of infrastrucutre to Amazon. The most basic of setups would involve the following:

- Create a VPC
- Create a public and private subnet in said VPC
- Create a Internet gateway (for ssh access)
- Create a NAT gateway to allow access to the internet from ec2 instances in private subnet
- Create a custom route table to relate internet gateway for public
  - Need 0.0.0.0/0 and 10.0.0.0/16
- Create a custom route table to relate the nat gateway and allow private vpc to connect to it
- Create a bastion instance and allow direct access to the internet in public subnet
- Create x etcd instances in private subnet

## Important information

- Security Groups are "stateful" but Network ACLs are stateless
- Incoming tcp traffic (e.g. ssh) can reply back with epheremal ports

## SSH commands
chmod 400 /path/to/pem/file
ssh-add "/path/to/pem/file"
ssh -A -i "/path/to/pem/file" username@public_ip_of_bastion_server
ssh username@private_ip_of_app_server