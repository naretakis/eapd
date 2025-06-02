# Preparing to run the Infrastructure as Code
Provisioning infrastructure with Terraform
First, you will need to download Terraform 13.1
### Downloads
| OS | Download Link |
| --- | --- |
| Linux | https://releases.hashicorp.com/terraform/0.13.1/terraform_0.13.1_linux_amd64.zip |
| Mac | https://releases.hashicorp.com/terraform/0.13.1/terraform_0.13.1_darwin_amd64.zip |
| Windows | https://releases.hashicorp.com/terraform/0.13.1/terraform_0.13.1_windows_amd64.zip |

Other OSs are avaiable from https://www.terraform.io/downloads.html.  
Next you will need to get the terraform.tfvars file from Bill. Hopefully in the future this step will change to not be reliant on a person.  

# Running the Infrastructure as Code
Place the tfvars file in the root terraform directory in the eAPD repo.  
You should then be able to run the infrastructure build with these commands:  
`terraform init`  
Review the output of the next step to make sure that terraform is doing what you want it to do:  
`terraform plan`  
If the terraform plan looks good, then run  
`terraform apply`  
The new infrastructure will be up and running in a few minutes.