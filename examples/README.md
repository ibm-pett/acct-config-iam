# IBM Terraform configurations for IBM Cloud Identity and Access Management (IAM)

This repository contains a collection of Terraform configurations for configuring IBM Cloud accounts using [Identity and Access Management](https://cloud.ibm.com/docs/account?topic=account-userroles) (IAM).

## Configurations

| Name | Description |
| ---------------- | ---------------- |
| [acctmgrs](https://github.com/ibm-hcbt/acct-config-iam/tree/master/acctmgrs) | Create an access group for account management and add users to make them account managers. |
| [partner-sandbox-acct-setup](https://github.com/ibm-hcbt/acct-config-iam/tree/master/partner-sandbox-acct-setup) | Create resource and access groups, service id and activity tracker |
| [partner-sandbox-randagroups](https://github.com/ibm-hcbt/acct-config-iam/tree/master/partner-sandbox-randagroups) | Create resource and access groups. |

## Run from a schematics workspace

1. Create a *schematics* workspace on your local cloud account
2. List https://github.com/ibm-hcbt/acct-config-iam/examples/partner-sandbox-acct-setup under "GitHub, GitLab or Bitbucket repository URL"
3. Leave git access token blank since this is a public repo
4. Change terraform version to 0.12
5. Save workspace settings
6. Enter resource group, access group and service id names in workspace options.
7. Click "Save Changes"
8. Select "Generate Plan" option at top right of page, when that finishes
9. Select "Apply Plan" option at top right of page
10. Verify that the resource group has been created by going to the "Manage", "Account", "Resource Groups" page
11. Verify that the access groups have been created by going to the "Manage", "Access (IAM)", "Access groups" page
12. Verify that the service id has been created by going to the "Manage", "Account", "Service Ids" page

## Run from local Terraform client

#### 1. Make sure Terraform is properly installed on your system see [Terraform Installation Instructions](https://ibm.github.io/cloud-enterprise-examples/iac/setup-environment/#install-terraform): 

#### 2. Create an IBM Cloud API Key
```
ibmcloud login --sso
ibmcloud resource groups
ibmcloud target -g RESOURCE_GROUP_NAME

ibmcloud iam api-key-create TerraformKey -d "API Key for Terraform" --file ~/.ibm_api_key.json

export IC_API_KEY=$(grep '"apikey":' ~/.ibm_api_key.json | sed 's/.*: "\(.*\)".*/\1/')
```
#### 3. Create an IBM Cloud Classic Infrastructure API Key
refer to [Managing classic infrastructure API keys](https://cloud.ibm.com/docs/account?topic=account-classic_keys). Ensure you create the key for the account you are setting up. 

#### 4. Set environment variables

Either export these variables or update the credentials.sh.template file to include

```bash
export IAAS_CLASSIC_USERNAME="< Your IBM Cloud Username/Email here >"
export IAAS_CLASSIC_API_KEY="< Your IBM Cloud Classic API Key here >"
export IC_API_KEY="< IBM Cloud API Key >"
```

If you updated credentials.sh.template, rename it to credentials.sh and execute:

```bash
source ./credentials.sh
```

#### 5. Install these configurations using the standard Terraform process

- From a command line, change to the configuration's directory
- Modify the `terraform.tfvars` file
- Run `terraform init` to initialize Terraform
- Run `terraform apply` to install the configuration

## Steps to set up a Partner Sandbox account

Refer to [Sandbox Setup Instructions](./README_SANDBOX.md) for steps to use these TF modules to set up a Cloud Pak Sandbox.
