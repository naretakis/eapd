# Infrastructure Contingency Plan - DRAFT

In this document you will find our plans for recovering from an infrastructure emergency. Our infrastructure is currently provisioned by CircleCI leveraging a BASH script that contains awscli commands. This script takes environment variables fed to it from CircleCI or through the command line. It then builds out either the production instance or the staging instance, depending on the environment variables, and connects it to the corresponding database. Here are our plans for Infrastructure emergencies.

## Infrastructure Emergencies that require rebuilding an instance
1a. Log into the CircleCI interface  
1b. Locate the last successful production release  
1c. Re-run the last successful production release  
1d. After CircleCI reports that the build is complete, wait a few minutes  
1e. Check the site AND try to log in  

## Infrastructure Emergencies that require rebuilding an instance without CircleCI
2a. Make sure you have the latest version of master from the eAPD GitHug repo  
2b. Change directories to the /bin/prod-deploy  
2c. Run the aws.sh script with the appropriate flags, documented in the file  
2d. Check the site AND try to log in  

## Recover RDS PostGres DB
* [[ Database Recovery Plan ]]

* Currently there are pieces of our infrastructure/networking that we do not control and in the event of a total failure of our AWS region, low risk, we would be at the mercy of outside entities to provision a new environment for us.
