# Create Dev Okta Setup

### Create Dev Okta Account

1. Go to [https://developer.okta.com](https://developer.okta.com/) and click the Go to Workforce Identity Cloud docs button or click the X in the upper right.

![CleanShot 2023-04-13 at 16.49.47.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/401A91FB-7D43-41F9-9383-DA8BE5C73BBE_2/4N7SrV2Xr2s9ozoTF6GylL5oxyupcOKm3bAYhxojSkUz/CleanShot%202023-04-13%20at%2016.49.47.png)

2. Click the Log in button.

![step2.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/898F983C-314A-4886-9BED-59F68A0652A6_2/Pjp9WSG2CkQSFvKwxg5Tz8hx0Zl5kEm4xH5rpwyHhz4z/step2.png)

3. You can choose however you would like to authenticate.

![CleanShot 2023-04-13 at 16.53.25.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/79228F26-59DD-4202-A253-DA0A3792FB64_2/8FKExXzIGCxhLCQnaEimmy63ZamFSUfRxLvpj9pYLlUz/CleanShot%202023-04-13%20at%2016.53.25.png)

### Create New Okta Application

1. Once logged in, click Applications > Applications in the side navigation.

![step4.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/FAAB05B3-7A5C-4A82-98DD-63867B746900_2/lrDR2IL0SD18iPNxxtMMIXntQDpiKypp8HxDO8lytesz/step4.png)

2. Click the Create App Integration button to create your new app. Your new account with come with some default applications, but this project requires a SPA application.

![CleanShot 2023-04-13 at 14.12.22.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/D2B1C7EB-B62F-424A-AEAD-C9CC549B8F57_2/2sVuVoDnD3LH1VxvDTAIJJrVGlR7x9q5ARpYpxSL6vEz/CleanShot%202023-04-13%20at%2014.12.22.png)

3. In the modal that opens, select OIDC and Single-Page Application and click the Next button.

![CleanShot 2023-04-13 at 16.57.27.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/E468ADB2-F740-4FBC-B182-17AB2F1346B0_2/qcSMI2xxOrWuJAgAj1cODy2VJpae2wLnH0ERgY5HrVsz/CleanShot%202023-04-13%20at%2016.57.27.png)

4. Name your application.

![step27.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/F8DEC24D-BB70-4A92-86D9-D556224C104A_2/QgwVsSIdVm92EVmqnkCpI5BCBbZPRXAEIBGlhF9F3BAz/step27.png)

5. Add the following urls, these are the urls you will need for local development. If the site is hosted somewhere else use those urls.  

**Sign-in redirect URIs:** 
- http://localhost:8080/implicit/callback
- http://localhost:8001/implicit/callback
- http://localhost:8081/implicit/callback  

**Sign-out redirect URIs:** 
- http://localhost:8080
- http://localhost:8001
- http://localhost:8081

![step28.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/79A96041-CB1C-4B2F-A864-F8D9AAC50843_2/xt1RYQ6ncdqmbM6VHCjycumpAnKYzPGQfUY4yjBUZTUz/step28.png)

6. Click the radio button next to Enable immediate access with Federation Broker Mode and click the Save button.

![step29.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/FC041295-1B50-4967-85C5-DC7C8871E1C4_2/RKmNxyGGutFy3hTsRg5xACrizwiEyzUAy9fLHmR1Vu4z/step29.png)

7. Your new application should appear in the Applications list. Add an environment variable OKTA_CLIENT_ID and set it to the Client ID beneath the new Application. Then, click on the new application name to open the application details.

![CleanShot 2023-04-13 at 17.14.57.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/1A76BE14-11EF-4DC5-95F2-CE2F3C3BCD72_2/fxJNdYLAy6RI03Uhcfk7M1H0iEFc9mhVNxp6Evy5Q9Ez/CleanShot%202023-04-13%20at%2017.14.57.png)

8. Click on Okta API Scopes tab. The list will show all available scopes. Leave the default scopes granted. Click ✔️Grant next to the following scopes:

- okta.clients.read
- okta.users.read
- okta.users.read.self

The image below shows the scopes already granted.

![CleanShot 2023-04-13 at 15.37.11.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/C389D357-37CC-4BA9-A2CC-4A3B8A01431C_2/z9DbY1HrTpj32bkJd3WEkBTtHAJEh5bSyrQ7jJ5MZ1Yz/CleanShot%202023-04-13%20at%2015.37.11.png)

### Create the API Key

1. Click Security > API in the side navigation.

![step8.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/E95A0FA9-B96F-4D08-B19E-7B39BD609057_2/Z0VdF0buPTDWN9bqOzlSPzlAfu34qedcnxDa3CDF6uwz/step8.png)

2. Create an environment variable named OKTA_AUDIENCE and set it to the value under the Audience header. It defaults to `api://default`. Create an environment variable named OKTA_DOMAIN and set it to the domain from the Issuer URI. Create an environment variable named OKTA_SERVER_ID and set to the last part of the URI. This defaults to `default`.

![CleanShot 2023-04-13 at 17.21.53.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/A7618AC4-0D52-4902-953F-00F7B5A9109A_2/U7jNTncCSLtrhLmDfKOvxq2Mc7Q5GFi2dDNvqiHCnMEz/CleanShot%202023-04-13%20at%2017.21.53.png)

3. Click the Tokens tab. Then, click the Create token button.

![step10.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/AF566553-33FC-4969-A59C-D74E3E33E5C8_2/9TUimSoyKclvyAjQq8HWfu9kcv1b7IFLRAWJxJDWr7wz/step10.png)

4. A modal will open. Name your token. Then, click the Create token button.

![step11.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/C9E60360-DBB9-4D0F-8F6F-BDE41D6427F6_2/uUhPVJH9sFmmaDLHvSFikMmWhy4TYXeVbylhS4fubwEz/step11.png)

5. Copy the Token Value that appears, because you will not be able to see it again. Then, click the OK, got it button.

![step12.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/073C97B5-971E-4BC0-AA0E-4AB2FDFB89CB_2/Y9Sx4mMzXgXYERWpw0US1PAeOZvbGjATbPeNOVURfe0z/step12.png)

6. Click the Trusted Origins tab. Then, click the Add origin button.

![step18.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/826EA99B-E57E-4B74-8F2A-B587FC6749F1_2/CGybYVuyMLaNXyma1yxOAXyGNiK6tgPBLuG9tFQyo00z/step18.png)

7. Add the url for your web server. The project sets the default web url to `http://localhost:8080`. Click the radio buttons next to Cross-Origin Resource Sharing (CORS) and Redirected. Click the Save button.

![step30.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/606F9720-4E03-4589-BECB-DC71CEEACBDF_2/Q9yUwFidTbmA3zYZSLs6OEI1erGZ8tSVipCzyWVmqosz/step30.png)

8. Click the Add origin button again. Add the url for your API server. The project sets the default API url to `http://localhost:8081`. Click the radio buttons next to Cross-Origin Resource Sharing (CORS) and Redirected. Click the Save button.

![step31.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/613A071B-9625-4407-AEDD-5B9CACB77D28_2/lhp6zR3jUw3hLqkkxyXeM6x2xq5XNSZLvCQa5ldeD9oz/step31.png)

### Add Test Users

1. Open the file `documentation/eAPD_Users.csv` and update the email addresses. They need to be actual email addresses that you have sustained access to, because they will be used in the event of updating passwords, getting one-time passwords, reseting locked accounts, etc. The development team used the Gmail trick of adding +something into your email address. For example, a person with the email address example@gmail.com could use example+stateadmin@gmail.com to create a unique email for the State Admin user. Make sure the file is saved in csv format.  **Explanation of Test Users:**

| Username        | Usage                                                                                                                                                                                                | Role             | Affiliation Seeded?        |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | -------------------------- |
| em@il.com       | Standard testing user                                                                                                                                                                                | State Admin      | Yes                        |
| fedadmin        | Testing as a Federal Administrator user                                                                                                                                                              | Fed Admin        | Yes                        |
| stateadmin      | Testing as a State Administrator user                                                                                                                                                                | State Admin      | Yes                        |
| statestaff      | Testing as a State Staff user                                                                                                                                                                        | State Staff      | Yes                        |
| statecontractor | Testing as a State Contractor user                                                                                                                                                                   | State Contractor | Yes                        |
| sysadmin        | Testing as a System Administrator user                                                                                                                                                               | System Admin     | No, added via LaunchDarkly |
| requestedrole   | Testing as a user who has requested a role that hasn't been reviewed yet                                                                                                                             | N/A              | Yes                        |
| deniedrole      | Testing as a user who had their role requrest denied                                                                                                                                                 | N/A              | Yes                        |
| revokedrole     | Testing as a user who had their role revoked                                                                                                                                                         | N/A              | Yes                        |
| norole          | Testing as a user who does not have any roles to test the requesting roles process                                                                                                                   | N/A              | No                         |
| expiredadmin    | Testing as a user whose State Administrator role has expired (logging in as the user should revoke their role)                                                                                       | State Admin      | Yes                        |
| pendingadmin    | Testing as a user who has an approved State Staff role and has a valid State Administrator Certification letter, this can be used by the Federal Administrator user to approve a State Administrator | State Staff      | Yes                        |
| betauser        | Testing as a user who is a Beta User in LaunchDarkly                                                                                                                                                 | State Staff      | Yes                        |
| notingroupmfa   | Testing the error message for a user not in our Okta group                                                                                                                                           | N/A              | No                         |
| lockedout       | Testing the error message for a user who has locked their account with too many failed login attempts                                                                                                | N/A              | No                         |
| expired         | Testing the error message for a user with an expired password                                                                                                                                        | N/A              | No                         |
| mfa@email.com*  | Standard testing with MFA required                                                                                                                                                                   | State Staff      | Yes                        |
| lockedoutmfa*   | Testing the error message and login flow for a MFA enabled user who has too many failed login attempts                                                                                               | N/A              | No                         |
| resetmfa*       | Testing the flow for setting the MFA for a user who requires MFA and doesn't have one set                                                                                                            | N/A              | No                         |
| norolemfa*      | Testing as a MFA enabled user who does not have any roles to test the requesting roles process                                                                                                       | N/A              | No                         |
| expiredmfa*     | Testing the error message for a MFA enabled user with an expired password                                                                                                                            | N/A              | No                         |

*You don't need to add the MFA accounts if you aren't using MFA with your site


2. Before we add users, we need to removed the Okta profile default of requiring logins to be in email format. Click on Directory > Profile Editor in the side navigation.

![CleanShot 2023-04-14 at 12.27.59.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/1E96A3F3-0873-47BB-87B8-9B3511F7DA64_2/yEjpjfYH3rVhRAY9qyXTRzKJmn3VY2Pkd661CMV4TZ8z/CleanShot%202023-04-14%20at%2012.27.59.png)

3. Click on User (default) in the Profile list.

![CleanShot 2023-04-14 at 12.28.50.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/BFA6FF6F-EAB8-4DA8-A396-1B8CB602A41B_2/f0sofkyHrqxnV2nK6Sx7CJ9MFxSli5PZIBXIyxIVzK8z/CleanShot%202023-04-14%20at%2012.28.50.png)

4. Click on the i button in the Username row.

![CleanShot 2023-04-14 at 12.29.18.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/78D78044-2BAA-43BF-9084-F3FD152BD48D_2/n6nA2en59XKIDxxveECHA6A8ZQmtZbtKQ3XBduQy2icz/CleanShot%202023-04-14%20at%2012.29.18.png)

5. Change Format restrictions to None. Click the Save Attribute button.

![CleanShot 2023-04-14 at 12.29.52.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/409AB780-8BA3-48C2-9E41-0240C464B781_2/HjEaFBnfBU3p5rkGfudOgz8tWriM8E9k9EIxX6xtt3Yz/CleanShot%202023-04-14%20at%2012.29.52.png)

6. Click Directory > People in the side navigation.

![CleanShot 2023-04-13 at 14.13.10.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/5E803672-58DA-4134-84B7-E43B0A0006B6_2/Y7rGoYqxFOaJbJ2vtjGNONVkaDKQVKDBzei6cs3tsc0z/CleanShot%202023-04-13%20at%2014.13.10.png)

7. Click the More actions button.

![CleanShot 2023-04-13 at 13.31.33.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/B4AA1CE3-6548-4938-A77F-AA1DB7FD2CD5_2/4ExZsy76e1dK7uOkarsA3YF0mIlfyii0xWr8V4RV1Fsz/CleanShot%202023-04-13%20at%2013.31.33.png)

8. Click the Import users from CSV item in the dropdown list.

![CleanShot 2023-04-13 at 13.32.39.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/95FA421C-491F-48DC-9EF0-AB9D04C2DFCF_2/RQWHb1Jz7Qq5LlpZDoKnUbWexqyyae1VX4VCAoF8hDoz/CleanShot%202023-04-13%20at%2013.32.39.png)

9. Click the Browse button. Navigate to the eAPD_Users.csv file.

![CleanShot 2023-04-13 at 17.43.53.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/18430602-39B3-4F9F-A17C-07DEC5FCE45F_2/80yu43n8UOFyxyGC0raTuJpMEqYEdYnBxo0B3ylPFLkz/CleanShot%202023-04-13%20at%2017.43.53.png)

10. Click the Upload CSV button. The modal will change to show the progress of parsing the file.

![CleanShot 2023-04-13 at 17.44.21.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/98F81B2F-21F4-4907-BBDD-818068C002F5_2/z5Fp6Ibq2g7s5Y3CXvKvsURee08VxY6E1JuFgnqFmycz/CleanShot%202023-04-13%20at%2017.44.21.png)

11. Click the Next button.

![CleanShot 2023-04-13 at 13.33.23.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/0FBC816B-47FD-4B3A-8A52-8F4CB2FF7FEF_2/pjTbd1Q3Bv5AEEmFCYVy422ZqnDrpaz1OIWXCZAyEWAz/CleanShot%202023-04-13%20at%2013.33.23.png)

12. Click the checkbox next to Automatically activate new users. Then click the Import Users button.

![CleanShot 2023-04-13 at 13.25.01.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/72817AA8-BB27-4915-A6A7-79E2E2858AF0_2/R7T338CpkeocslSoCFxeW4gaVxKmRbVb3wz76j8hyAYz/CleanShot%202023-04-13%20at%2013.25.01.png)

13. The modal should update to show that all users have been imported successfully. Click the Done button. 

If there are issues with the upload, there will be an option to download the CSV with error messages added to it. You can remove the successful rows and then fix the errors and try the upload again.

![CleanShot 2023-04-13 at 13.34.55.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/520CE1E2-9BE6-4772-A7E3-709514AE9D51_2/piH3Xv4LwzxSzTFmOH8nCnSd62DVGVc5xn7soMTvMcYz/CleanShot%202023-04-13%20at%2013.34.55.png)

14. You will get emails for all of the new accounts with links for setting the passwords. Create passwords for each account and save them for future use. Once all of the passwords have been set, the Status of all of the accounts should be Active.

![CleanShot 2023-04-13 at 13.51.37.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/B1C32F35-6D2F-4C82-A6DA-DEE9AE907416_2/CNsJ93RTsAYtuiH68984ZEM7Yyk6xLzAZLgHffZwJsAz/CleanShot%202023-04-13%20at%2013.51.37.png)

15. Two accounts are used to test the expired account error messages, so they need to have their passwords expired. Click on the Password Expired account.

![CleanShot 2023-04-13 at 13.55.57.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/7C2331B0-DCF3-4EAF-93DA-87A56242B470_2/x1tXIypuF6XH5SpCLJqykOKzp50DydxsXyCNHSGupdMz/CleanShot%202023-04-13%20at%2013.55.57.png)

16. Get the user's ID from the url `https//[OKTA_DOMAIN]/admin/user/profile/view/[userID]` in the browser.
17. Open Postman/Insomnia/Terminal, set the Authorization header to `SSWS [OKTA_API_KEY]`, braces are just to distinguish that the value needs to be replaced. Then `POST` to `[OKTA_DOMAIN]/api/v1/users/[userID]/lifecycle/expire_password` to manually expire the password.
18. The account should now show that the password is expired. Repeat steps 10-12 for the Expired MFA account.

![CleanShot 2023-04-13 at 14.00.28.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/FE13F0AD-6BC3-4FD6-976C-EBDBD6175F93_2/4CHcfw0ravJuf7VEL3oByosxwcifOQzR3tsgqkTVMTQz/CleanShot%202023-04-13%20at%2014.00.28.png)

### Create User Groups

1. Click Directory > Groups in the side navigation.

![CleanShot 2023-04-13 at 14.13.54.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/684D4C39-0906-4A17-9760-7D3D6B14A9A6_2/tuwQnWj9FIX1h71r4RMO7wNlgCL20MoUJaqFn6Pv2Qsz/CleanShot%202023-04-13%20at%2014.13.54.png)

2. Click the Add group button.

![CleanShot 2023-04-13 at 14.14.14.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/8587A6D3-3F20-4FC6-9351-A4B0C9AC603C_2/OGz5oa1mh29uEYEmye73iIZtT5xYDMdxuopxFB3TCN4z/CleanShot%202023-04-13%20at%2014.14.14.png)

3. Create a group for eAPD Users. Click the Save button.

![CleanShot 2023-04-13 at 14.15.14.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/D6DCE85D-9580-4130-8F6E-635F95F0E56C_2/eQCZQrMseedwP6mQlzq9SsmT6Vswsqbb0jUYM5Ky0koz/CleanShot%202023-04-13%20at%2014.15.14.png)

4. Click the new eAPD Users group.

You might need to manually refresh the page to see the new group.

![CleanShot 2023-04-13 at 14.15.43.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/1176C1C1-3C19-4A6C-93D6-7B95A16BA5AC_2/j5kzSGie8cPxRmEEUF47pg1bjm1YyYsAeV8xiTdRGy8z/CleanShot%202023-04-13%20at%2014.15.43.png)

5. Click the Assign people button.

![CleanShot 2023-04-13 at 14.16.25.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/74CA87EC-4BCE-4827-9695-4D28F84E885D_2/GaaMENxrbejpW9L2srrou5iZTf85cwyNmzNQf9OkOKkz/CleanShot%202023-04-13%20at%2014.16.25.png)

6. Click the + sign next to all of the users, except NotInGroup MFA, to add them to the group.

![CleanShot 2023-04-13 at 14.17.06.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/FE4B3D25-EF90-4260-9DFC-9CC0BF433CA2_2/quDtqjGPiVoidzw0pnHdVW87lno9Hzp3yYDnePAMXpAz/CleanShot%202023-04-13%20at%2014.17.06.png)

7. Click the Done button.

![CleanShot 2023-04-13 at 14.18.43.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/AE6E3111-7161-43AA-AAC2-8B9C0FD8A55F_2/a2O2mpmCkI2r6hEBA1q9RO2zvxXXJXCM0u3HUZPtS30z/CleanShot%202023-04-13%20at%2014.18.43.png)

8. Repeat steps 5-7 until all of the users, except NotInGroup MFA, have been added to the eAPD User group. There should be 20 of these users in this group. If NotInGroup MFA is in the group some of the Cypress tests will fail. If they were added, you can remove them by opening the group and clicking the X button in the row with their name.

9. Repeat steps 2-7 to create an eAPD MFA group to hold the users needed to test MFA functionality. Add all of the users with MFA in their name to this group. There should be 6 of these users in this group.

![CleanShot 2023-04-13 at 16.35.44.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/965572CF-5D66-4CFC-854E-0AB23571F893_2/xAniQd8s6YTTx3HqaArVTMlCBFbLCk50tqkYPDkw8rgz/CleanShot%202023-04-13%20at%2016.35.44.png)

![CleanShot 2023-04-13 at 16.36.55.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/4B888E8C-E91D-46C5-B0E6-D4DC4FE20C6B_2/wYlxfYIzDPjAFLocjyJHAw3xpD5ohCKN56Ztp4jUmdoz/CleanShot%202023-04-13%20at%2016.36.55.png)

### Add eAPD User Group to the Application

1. Click Applications > Applications in the side navigation.

![CleanShot 2023-04-13 at 14.21.43.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/4D426666-51E4-448F-B0D9-ABB4499DBC1D_2/vDod9OY63w3LiTGZ6iktnxpKqG3McK7Bw7drS4seCJgz/CleanShot%202023-04-13%20at%2014.21.43.png)

2. Click on the application.

![CleanShot 2023-04-13 at 14.22.12.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/1A599B67-BDD2-41C6-A65D-D2BD96A70B92_2/Rd3Wh9xqWifzOgyQS3fvAtzaNpDHp5Boyo93WADMml0z/CleanShot%202023-04-13%20at%2014.22.12.png)

3. Click the Assign button.

![CleanShot 2023-04-13 at 14.23.35.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/625D6836-E267-4491-BD4B-14CCF776DE82_2/evxhhS7LxoqBQyZikxJIug4L6hhFiAIhIo4VBlYDfOEz/CleanShot%202023-04-13%20at%2014.23.35.png)

4. Click the Assign to Groups item in the dropdown lists.

![CleanShot 2023-04-13 at 14.24.00.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/AD2F9BF7-6014-4CAE-89C3-80A364B15764_2/NbBTPy0byrKV5iNTr8WPUm1Ib5j7Jq8h7DEYIlJKci8z/CleanShot%202023-04-13%20at%2014.24.00.png)

5. Click the Assign button next to the eAPD Users group.

![CleanShot 2023-04-13 at 14.24.22.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/BF873B71-7FC9-4ED0-8C97-3AD7FE314EEA_2/PQTkQEA8SkktYkEgF9xfAWzOGjN0CCifaw1eB2hoylsz/CleanShot%202023-04-13%20at%2014.24.22.png)

6. Click the Done button.

![CleanShot 2023-04-13 at 14.24.53.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/B3EA0A61-7A96-4C45-BAEE-2A1F5B9CCF19_2/hKgS1k23EiNNTRXX6SWtAUIlrD6AVj59Ghkl8FPLx3oz/CleanShot%202023-04-13%20at%2014.24.53.png)

### Set Up Failed Login Attempt Limit

The CMS Okta policies only allows users 3 failed log in attempts before their account is locked out. The Cypress tests in `01-authentication/02-invalid-login-attempts.cy` expect this to be the case. A few settings have to be enabled as well to return the appropriate error message that the front end expects to see for failed login attempts and user lock outs.

1. Click Security > Authentication in the side navigation.

![CleanShot 2023-04-14 at 09.16.42.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/17DA1640-BA7A-4CA1-BC00-E3C12A609B94_2/OCzB3b4idepRxLbwRO4m5VtGedcPbzBLyBI81sP7aAcz/CleanShot%202023-04-14%20at%2009.16.42.png)

2. Click the Edit button on the Default Policy.

![CleanShot 2023-04-14 at 09.32.18.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/65839D9B-7EB0-489D-931A-FD231F13F3A9_2/7uoBvMIJEXiWn4DAG18VHn4V3ITss5pfODIVz4C3gVgz/CleanShot%202023-04-14%20at%2009.32.18.png)

3. Scroll down to Lock out and change Lock out user after _ unsuccessful attempts to 3. Click the checkbox next to Account is automatically unlocked after 60 minutes. Click the checkbox next to Show lock out failures. Click the checkbox next to Password expires after 120 days. Click the Update Policy button.

![CleanShot 2023-04-14 at 09.57.28.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/1A2C0ED1-BF66-4A42-BB87-2CC8523A2C34_2/xugyXOvpGLXwplfhXz8uwv4KgUjxYSxDsbu5zg1iBY8z/CleanShot%202023-04-14%20at%2009.57.28.png)

### Set Up MFA Requirements

The CMS Okta configurations require MFA for all accounts. We were allowed to have a group of users without MFA on the non-production environments. So the Cypress tests do not assume MFA requirements. However, the project is set up to handle MFA, if you would like to also require it. The instructions explain how to create a group where MFA is required and the rest of the accounts do not require it, for simplicity. The more secure method would be require MFA by default for all users and then creating and exempt group.

1. Click Security > Multifactor in the side navigation.

![CleanShot 2023-04-13 at 14.36.31.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/F56F2C27-B9A5-4657-9830-0F12AABF1010_2/wJfNO1coMnK64xv1x4JZDxVR6ijuqvu9EI0Cuj3D5Q4z/CleanShot%202023-04-13%20at%2014.36.31.png)

2. Click on the factors that you would like to use. Click the Inactive button on the factors you want.

![CleanShot 2023-04-13 at 16.23.33.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/810B84D8-33B8-4A6E-917F-9C44F1F2AF7F_2/nkPitoNbaoKR6Lx8m0KgEc9wSoded5JfOouj4uMDF7Ez/CleanShot%202023-04-13%20at%2016.23.33.png)

3. Click the Activate item in the dropdown list.

![CleanShot 2023-04-13 at 16.24.27.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/42D6EB26-6CA9-4E4E-84AA-B26B5F817F6D_2/P9HqI73MyEYIE7gTUulTDjkANePq5YXGjyiJp7KqW4Iz/CleanShot%202023-04-13%20at%2016.24.27.png)

4. Click the Factor Enrollment tab to see the active factors.

![CleanShot 2023-04-13 at 16.25.31.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/FBDA8744-E22A-4009-B537-94185DE6F127_2/irdZ2guhgczJz2A9yNVpDdI668fwMBeA4TrMTycir14z/CleanShot%202023-04-13%20at%2016.25.31.png)

5. Click Security > Authentication in the side navigation.

![CleanShot 2023-04-13 at 16.25.57.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/B70F7E20-FB67-45F4-99EF-51221EB6F393_2/8dl6c3SMumTGeOIOQ9yS3mqwl3Ad0kFQTOKVQn8z2wIz/CleanShot%202023-04-13%20at%2016.25.57.png)

6. Click the Sign On tab. Click the Add New Okta Sign-on Policy button.

![CleanShot 2023-04-13 at 16.40.11.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/73462123-DD6F-440A-B6EC-FF14A8FE9BDB_2/nyp6YyJeHJ5VL6nMFndGQUZRc7LZ4xLaqDQXkFF5zBkz/CleanShot%202023-04-13%20at%2016.40.11.png)

7. Create a policy and assign it to the eAPD MFA group. Click the Create policy and add rule button.

![CleanShot 2023-04-13 at 16.41.01.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/B19CE48B-F1B1-40C9-B55E-BDF7D6CE8779_2/m8sJBCoL3mv6GqoshqZqYWNcYbUkFdhcweF3vnL9Zucz/CleanShot%202023-04-13%20at%2016.41.01.png)

8. Click the radio button next to Required and Set time limit (Recommended). Click the Create rule button.

![CleanShot 2023-04-13 at 16.41.32.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/F4C053AE-1DCE-4F1C-B13F-94A349959905_2/ydYpWyow6R2LQONFsDor9CMxNvs8J9fGEL0AJfyEWocz/CleanShot%202023-04-13%20at%2016.41.32.png)

![CleanShot 2023-04-13 at 16.41.53.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/A894083D-2CCD-4973-B329-C4E1A03EAECB_2/0QCMw4eSVx90HhxfFyGNxd4FH5aQpGg6dSzldx1NwAwz/CleanShot%202023-04-13%20at%2016.41.53.png)

9. The new policy should be created and active.

![CleanShot 2023-04-13 at 16.42.33.png](https://res.craft.do/user/full/9eea51cb-f883-ebc6-3a7f-49723d90b872/doc/7DF32611-439F-4207-ADFD-294C470E8408/EB00FAF1-43A2-475C-A54C-EFB83F1CA9A4_2/A0eqxOye0QtKQa7njklSWFnUvgHnHQXU7yzx0Lq3xygz/CleanShot%202023-04-13%20at%2016.42.33.png)

