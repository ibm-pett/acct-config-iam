# IBM Terraform configurations for IBM Cloud Identity and Access Management (IAM)

This repository contains a collection of Terraform configurations for configuring Identity and Access Management (IAM) in IBM Cloud. These are focused on account management.

## Configurations

| Name | Description |
| ---------------- | ---------------- |
| [acctmgrs](https://github.com/ibm-pett/acct-config-iam/tree/master/acctmgrs) | Create an access group for account management and add users to make them account managers. |

## Variables

| Name | Description |
| ---------------- | ---------------- |
| acct_mgr_admins_access_group_name | The name for the new access group |
| acct_mgr_admins_user_ids | The users to add to the access group |

## Use

Install these configurations using the standard Terraform process:
- From a command line, change directory to the configuration's directory
- Modify its `terraform.tfvars` file
- Run `terraform init` to initialize Terraform
- Run `terraform apply` to install the configuration
