## Emergency Deploy to Staging
These instructions are for using the new option to deploy directly to staging to test more rapidly test things that do not break on a Preview Build, but do break when deployed to staging. This is the ONLY scenario in which this should be used.

## Steps to Deploy Directly to Staging
1. Make sure the branch that you are deploying to staging is up to date with Main
2. Make the fixes to the branch you want to deploy to the Staging environment
3. Commit those changes to your branch
4. Create a tag using the following pattern (after you've commited, but before you've pushed)  
``` git tag -a rc4.6.3 ```  
Release Candidate major version, minor version, patch version
5. Push, you must specify that you want to push the tag as well  
``` git origin push rc4.6.3 ```  
6. This will run the deploy to staging jobs in CircleCI
7. After the deploy has completed, log into the staging URL and test the app
8. Once changes are fixed follow normal procedure of merging work