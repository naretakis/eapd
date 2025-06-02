## Generating CSRs (Certificate Signing Requests)
There are several different ways to do this, you can use a website, you can run openSSL commands
More steps

### Requesting the New Certificates
From CMS Help Desk circa 2022
```
You can get the SSL certificate through the IUSG-DOM team by:

1. Submitting a request via the CMS Connect portal

    Select Request then click “View All”
    Select “Operations and Hosting”
    Select “SSL Certificates”
    Choose the appropriate certificate
    Complete the form
    Click “Submit” when completed

2. Sending an email to the CMS-DOMSSLCert mailbox at DOMSSLCert@cms.hhs.gov

Required information:

    Name of requestor
    CMS business owner component
    CMS business owner POC
    Email contact
    The certificate signing request (CSR) file.

For more detailed instructions, please refer to Requesting SSL/TLS certificates

Once the SSL certificate is obtained, please import it to AWS Certificate Manager (ACM). To learn more about how to use the ACM to manage your certificates feel free to review our Importing certificates into ACM

CMS Cloud does provide one-time training to teach your team how to create a CSR, upload the new certificate into ACM, and push the certificate to your systems. Please comment in this ticket to take advantage of the training.
```

## Importing the Certs
1. Log into AWS and go to AWS Certificate Manager, ACM.
2. Click on Import
3. Copy and paste in the certificate you received from the cert issuer
4. Copy and paste the key from the CSR that you generated as a part of requesting the certificate
5. Copy and paste the Certificate chain that you received from the cert issuer

## Using the Certs
1. Once the certificate has been navigate to CloudFront
2. Click Distributions and pick/click the domain/distribution where you want to install the new cert
3. Under General > Settings and pick the new cert from the "Custom SSL certificate - optional" drop down
4. Next navigate to EC2 > Load Balancers and choose the load balancer you need to update the certs on
5. Navigate to the Listerners Tab and select the Listener you want to edit and click Edit next to Add Listener
6. Navigate to Secure Listener Settings > Default SSL/TLS Certificate and select the new cert from the drop down
7. Go back to EC2 > Load Balancers, select the same Load Balancer and go back to the Listeners tab
8. Click View/Edit Certificate on 443
9. Click the top + at the top of the page, select the new certs, remove the old certs