Cloudformation templates
========================

vpc-base.yml - template for creating a VPC with 2 public and 2 private subnets in different availability zones. Private subnets have outband Internet access through a NAT gateway. Bastion hosts on public subnets reachable from the internet.

Usage
-----

Validating the template:

	$ aws cloudformation validate-template --template-body file://vpc-base.yaml
	
Create stack
  
  $ aws cloudformation create-stack --stack-name poc-stack --template-body file://vpc-base.yaml --parameters ParameterKey=KeyName,ParameterValue=<KEY_NAME> ParameterKey=NamePrefix,ParameterValue=<PREFIX>
  
KeyName parameter - name of the keypair to be used for bastion hosts.
NamePrefix parameter - Prefix for all named resources.

Note: Adjust CIDR blocks of the VPC and the subnets based on requirements.
