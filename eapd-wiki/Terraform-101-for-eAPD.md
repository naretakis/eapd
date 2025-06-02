# Terraform 101 for eAPD
## What is Terraform?
Terraform is an Infrastructure as Code (IaC) tool. Using IaC allows us to have an automate-able, reproducible, and reliable infrastructure definition. Instead of provisioning things by hand or through a collection of scripts, IaC allows for blueprinting your infrastructure as you would any other code. 

## Structure
Our Terraform is leveraging a module structure to make the overall code base easier to manage. Instead of defining everything within a single file, things like EC2 instances are defined in a directory called "instances" within the modules directory. Within the instances directory files can be found for managing the EC2 instances in our environment.  
Structure Example:  
```
/
/providers.tf
/main.tf
/variables.tf
/terraform.tfvars
/modules
/modules/instances
/modules/instances/example1_name.tf
/modules/instances/example2_name.tf
/modules/instances/variables.tf
```

In the root Terraform directory there will be several purpose specific files; providers.tf, main.tf, variables.tf, and terraform.tfvars.  The providers.tf file is where the information detailing our Infrastructure provider (AWS) is stored. The main.tf file serves dual purposes; first it makes the root Terraform aware of the modules, secondly it passes the variable values from the root Terraform to the modules. Root Terraform and the modules are black boxes and unaware of what is going on within each other without this linking/passing. The last .tf file is the variables.tf file and its purpose is to declare variables so that the root level Terraform is aware of the variables that are going to be used. The last file in the root level is the tfvars file, this is where you define the variables you declared in in the variables.tf file. The terraform.tfvars file is also a "hidden" file and should NOT be included in GitHub. This allows it to store secrets without exposing them publicly.   
  
In the modules directory there are multiple other directories to organize the other pieces of our infrastructure. For example, the instances directory. This directory will hold .tf files that define the EC2 instances in our infrastructure. example1_name.tf will hold the configuration required to provision the example1 EC2 instance and the example2_name.tf file will hold the configuration required to provision example2 EC2 instance. However, both of these files rely on the root level main.tf file to pass the variable values from the root level terraform.tfvars file to the instances module, because the root level Terraform and the instances module level Terraform are block boxes unto each other, there also needs to be a second variables.tf file in the instances module that will declare the variables that are going to be used by those instance .tf files.  

## Reviewing
To review Terraform code, I recommend running 3 commands, in this order, in the terraform root directory:
```
terraform init
terraform validate
terraform plan
```
`terraform init` Initializes Terraform and allows it to prepare what it needs to run.  
`terraform validate` Checks the existing Terraform configuration and makes sure that it has nothing in it that would prevent it from running.  
**this step requires an up to date tfvars file**  
`terraform plan` This will make Terraform do a dry run of the actions, the output of the plan should reflective the actions/changes listed in the Pull Request.

## Notes
* Currently Terraform state is run locally, so when you run the Terraform state against your local Terraform you will get ALL of the actions Terraform is supposed to perform based on your last Terraform state or lack of state.  
* Future improvements include creating a centrally located Terraform state to address the above concern. When this is implemented a backend.tf file will be added to the root Terraform directory.  
* The current method of sharing secrets, and therefore the tfvars file, is via encrypted, password protected zip file. If/When you need/want a copy of the tfvars file please make it known.  