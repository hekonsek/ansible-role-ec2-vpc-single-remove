# Ansible Role - Removes EC2 VPN with a single public subnetwork

Removes EC2 VPN with a single public subnetwork (created using 
[https://github.com/hekonsek/ansible-role-ec2-vpc-single](ec2-vpc-single role)). It ensures that:
- EC2 VPC is removed
- EC2 Internet Gateway associated with it is removed
- single public subnetwork assigned to it is

## Compatibility

This playbook has been tested against Fedora 27.

## Requirements

Keep in mind that Ansible EC2 module requires you to have Boto installed: 

    sudo pip install -U boto

You can specify AWS credentials either in Boto file (for example `~/.boto`) or using environment variables:
    
    AWS_ACCESS_KEY_ID='yourKeyId' AWS_SECRET_ACCESS_KEY='yourSecretKey' ansible-playbook aws.yml

## Installation 

    ansible-galaxy install hekonsek.ec2-vpc-single-remove,0.0

## Role variables

- `vpc_name` - **Required** VPC name. It is also used as prefix for names of subnet, internet gateway and route table.
- `region` - AWS region to use. Default region is `us-east-1` i.e. the cheapest one.

## Example playbook

```
- hosts: localhost
  connection: local
  gather_facts: false
  roles:
    - { role: hekonsek.ec2-vpc-single-remove,0.0 }
```

## License

Apache 2.0