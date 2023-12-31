# Inteleccess_devops
# AWS Infrastructure Deployment

This repository contains AWS CloudFormation templates for deploying a network infrastructure with VPCs, VPN, and RDS.

## Templates

- **`vpc-template.yaml`**: CloudFormation template for creating VPCs with public and private subnets.
- **`vpn-client-template.yaml`**: CloudFormation template for deploying an AWS VPN Client.
- **`rds-template.yaml`**: CloudFormation template for provisioning an Aurora MySQL Serverless RDS instance.
- **`vpc-peering-template.yaml`**: CloudFormation template for creating VPC peering between two VPCs.

## Parameters

- **`shared-system-network-params.json`**: Parameters file for the shared system network VPC.
- **`dev-system-network-params.json`**: Parameters file for the dev system network VPC.
- **`vpn-client-params.json`**: Parameters file for the VPN client.
- **`rds-params.json`**: Parameters file for the RDS instance.

## Scripts

- **`install-openvpn-client.sh`**: Script for installing the OpenVPN client on your local machine.

## Deployment Steps

1. Deploy shared-system-network VPC:
   ```bash
   aws cloudformation create-stack --stack-name shared-system-network --template-body file://templates/vpc-template.yaml --parameters file://parameters/shared-system-network-params.json --capabilities CAPABILITY_IAM

2. Deploy dev-system-network VPC:
   ```bash
   aws cloudformation create-stack --stack-name dev-system-network --template-body file://templates/vpc-template.yaml -- 
   parameters file://parameters/dev-system-network-params.json --capabilities CAPABILITY_IAM

3. Create VPC peering:
   ```bash
   aws cloudformation create-stack --stack-name vpc-peering --template-body file://templates/vpc-peering-template.yaml -- 
   parameters file://parameters/vpc-peering-params.json --capabilities CAPABILITY_IAM

4. Deploy VPN client:
   ```bash
   aws cloudformation create-stack --stack-name vpn-client --template-body file://templates/vpn-client-template.yaml -- 
   parameters file://parameters/vpn-client-params.json --capabilities CAPABILITY_IAM

5. Deploy RDS instance:
   ```bash
   aws cloudformation create-stack --stack-name rds --template-body file://templates/rds-template.yaml --parameters 
   file://parameters/rds-params.json --capabilities CAPABILITY_IAM

7. Install OpenVPN client:
   ```bash
   ./scripts/install-openvpn-client.sh

## Name - Abhay Patel
## Roll Number  - 2001331540001 
## Email Id -  abhaypatel6794@gmail.com
