# CircleCI Contingency Plan

If you find yourself unable to run builds from CircleCI follow the below steps in order to use the scripts to build/rebuild staging and production instances. You will need the awscli and aws API credentials to run the build scripts.

1) Create zipped archive of the api/backend (This step is only needed if the artifacts in CircleCI are unreachable)
You can consult this URL for more information on manually building the app:
https://github.com/CMSgov/eAPD/wiki/Development-Environment  
* Clone the repo, 
```
git clone https://github.com/CMSgov/eAPD.git
```
* Change directories to be in the api directory
```
cd api
```
* Install via npm
```
npm install
```
* Create a zip file of the api directory
```
zip -r backend.zip api
```
* Place the zip file someplace that the app can retrieve it
Example: S3
  
  
2) Run the aws.sh script with flags
* You can consult the script itself in the eAPD repo at bin/prod-deploy/aws.sh. The steps are the same for Staging and Prod, the flags are what differ.
* Change directories to be in the eAPD repo at bin/prod-deploy
```
cd bin/prod-deploy
```
* Below is the name of the script, aws.sh, and all the flags that need to be add, but with example flag settings (you can’t copy and paste this and expect it to work)
```
./aws.sh --API_AWS_ACCESS_KEY_ID YOURAWSACCESSKEY --API_AWS_SECRET_ACCESS_KEY CORRESPONDINGSECURITYKEY --API_DATABASE_URL "postgresql://username:password)@postgres.rds.url.com/databasename" --API_FILE_S3_BUCKET location.of.frontend.files.com --API_PBKDF2_ITERATIONS 123456 --API_PORT 1234 --AWS_REGION us-east-1 --AWS_SECURITY_GROUP sg-securitygroup --AWS_SUBNET subnet-subnet --AWS_TARGET_GROUP "arn:aws:elasticloadbalancing:us-east-1:awsaccountid:targetgroup/loadbalancername/targetgroupid" --BUILD_URL "the.place.you.put.the.backend.zip.file.com/backend.zip" --ENVIRONMENT stagingorproduction
```
  
  
3) Check the application
* Check the site you just built
  
  
4) Manually launch the app with appropriate flags (Only necessary if logging into the App doesn’t work)
* You will need to add the node NODE_ENV flag for production and the DATABASE_URL depending on the environment you are connecting to
Example:
```
NODE_ENV=production DATABASE_URL="postgresql://username:password@url-for-the-appropriate-environment.com/database_name" npm start
```
  
  
5) Make sure you can log into the App
