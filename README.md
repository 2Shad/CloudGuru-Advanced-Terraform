# CloudGuru-Advanced-Terraform

### Prerequisites
- install terraform on AWS CloudShell using the [install_terraform_on_aws_cloudshell.sh](install_terraform_on_aws_cloudshell.sh) script.

## 1st Configuration
Here I built a simple AWS infrastructure with an EC2 machine with user_data to install apache during the build, added a security group in order for the apache server to be accessable, and made sure that the public IP of this EC2 instance is displayed on the terminal so that we don't need to find it ourselves.