### API Testing Tool

First, select an API Testing Tool. Currently, the tool used by the majority of the team is [Postman](https://www.postman.com/). 
#### Import using Postman 
1. On the left-hand side, select the Import button.
2. Using the code repository tab, select Github.  
**Voila, you have imported the Postman folder from Github!**

##### To Get Started 
###### 1. View Collections 
On the left-hand side, select Collections then hitech-apd. 
###### 2. Understanding Requests
At the heart of each request, there is an endpoint. The basic structure of an endpoint is the baseurl = PR, staging, production, and applicable directories.  
Examples: 
* {baseURL}}/apds
* {{baseURL}}/login
* https://staging-eapd.cms.gov/login

##### Happy Testing with whatever API Testing Tool!!!

### Resetting the environment

The steps to resetting an environment. First confirm that you are either functioning in either the Local Dev or Staging environments. Open your browser and the web tools. Log into the app on that environment you want to reset. Open the Network tab on the web tools. Filter on `me`. Click on one of the `me` entries and look for `authorization` in the `Request Headers`. Copy everything after `Bearer`. Open Postman, click on the `Authorization` tab. Select `Bearer Token` and paste what you just copied into `Token`. Then, you can run "Get list of user's APDs" which will let you know the "id" of the APD you want to update, pick an APD with a status that is not "archived," lastly run the "Patch new APD with sample data" which will overwrite the APD id of the environments existing data with the sample data in the patch.

- Confirm that you are in either the Dev or Staging Environments
- Get the JWT from the browser
- Put the JWT into Postman
- Get list of user's APDs (/apds)
- Patch new APD with sample data (/apds/{{created-apd-id}})

### Testing

You can test these changes by logging into the eAPD staging or dev website, editing the APD in your Dashboard and then running the "Patch new APD with sample data" endpoint again. Your changes should be reverted back to their original test data values.

### Assumptions
- You have required credentials/variables, these should be provided by the Postman zip file
- You have a functioning local Dev environment