# iac_docker_swarm
The code in here scratch-builds a Docker Swarm cluster in AWS.  It uses Terraform, Ansible, and a
little bit of Python to automate the build of the cluster.
## Terraform
Terraform is used to build and secure some AWS instances.  A provisioner is called on each of
the created EC2 instances that outputs the machine's IP address and purpose to a small text file.
A null provisioner (with a dependency set on the EC2 instances fires off a Python script
followed by an Ansible playbook to configure the instances and build the cluster.
## Python
The amount of Python involved here is very small.  It simply reads the small file generated by 
Terraform and creates an Ansible inventory file.
## Ansible
The Ansible playbook installs and configures Docker Swarm on the hosts created by Terraform.
