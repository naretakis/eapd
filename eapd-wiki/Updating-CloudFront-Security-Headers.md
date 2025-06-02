1. Log in to AWS
2. Navigate to AWS Lambda
3. Find the Lambda you want to update, identified by _staging and _production respectively
4. Make desired changes to the CloudFront Security Headers in the Code source area
5. Click Deploy
7. Click Actions > Publish New Version, add description of what the change is
> _Potential Gotcha, make sure you have chosen the correct CloudFront Distribution for the correct environment*_
8. This will navigate you to the new version, click back up one level to the Lambda you just changed so that you can deploy the changed you just made and published.
9. Actions > Deploy to Lambda@Edge (you will do this twice per Security Header changed)
10. Click the radio button to "Use existing CloudFront trigger on this function" and choose
```
    Cache behavior: *
    CloudFrount event: origin-response
    Include body: false
```
11. Repeat steps 8-10 and this time choose:
```
    Cache behavior: index.html
    CloudFrount event: origin-response
    Include body: false
```
> Note: If you are updating both Staging and Production CloudFront Security Headers you will need to "Deploy to Lambda@Edge" four times total.

> Note: The easiest way to identify the appropriate Cloudfront Distribution is to go to the CloudFront section of AWS, click on "Distributions" and look at the "Alternate Domain Names," then make a note of the Distribution ID.
