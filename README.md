# CloudGuru-Advanced-Terraform

### Prerequisites
- install terraform on AWS CloudShell using the [install_terraform_on_aws_cloudshell.sh](install_terraform_on_aws_cloudshell.sh) script.

## 1st Configuration
Here I built a simple AWS infrastructure with an EC2 machine with user_data to install apache during the build, added a security group in order for the apache server to be accessable, and made sure that the public IP of this EC2 instance is displayed on the terminal so that we don't need to find it ourselves.

## Default Tags
**Tags is always a Best Practice**

- **Makes it easier to find resources**
- **Groups resources of a specific solution**
- **Better cost analysis insights**
- **Allows configuration of granular permission**

## Authentication Methods

### Provider Configuration
```hcl
provider "aws" {
  region     = "us-west-2"
  access_key = "my-access-key"
  secret_key = "my-secret-key"
}
```


### Environment Variables
```hcl
provider "aws" {}

# Environment Variables:
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
AWS_REGION
```


### Shared Configuration and Credentials File
```hcl
provider "aws" {
  shared_config_files     = ["~/.aws/conf"]
  shared_credentials_files = ["~/.aws/creds"]
  profile                 = "prod"
}

# These files are generated from the command:
# aws configure
```


### Container Credentials
- **For ECS and CodeBuild (automatically set):**
  ```plaintext
  AWS_CONTAINER_CREDENTIALS_RELATIVE_URI
  AWS_CONTAINER_CREDENTIALS_FULL_URI
  ```

- **For EKS using IAM Roles for Service Accounts (IRSA):**
  ```plaintext
  AWS_ROLE_ARN
  AWS_WEB_IDENTITY_TOKEN_FILE
  ```


### Instance Profile Credentials and Region
- **Access through the Instance Metadata Service (IMDS).**
- **Both versions (v1 and v2) are supported.**


## Terraform State File

### Importance of a Backend in Terraform  
**What Do We Have so far?**

- **Local Store Backend**  
  State files are stored in the same local folder as the Terraform configuration code.

- **JSON**  
  The JSON file includes the current state of the resources created by Terraform.


### Importance of a Backend in Terraform  
**What's Wrong with That?**

- **Not ideal for collaboration with a team**  
- **Sensitive information may be included**  
- **If the file is lost, WE ARE LOST!**



## Terraform Backend

- **Centralizes the configuration**  
- **Protects the state file in case of an issue with your local machine**  
- **Enables better collaboration**
