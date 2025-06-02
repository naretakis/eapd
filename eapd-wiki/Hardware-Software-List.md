As of 07/09/2020
# Hardware
## AWS Infrastructure
### AMI
Name: (None)
* AMI Name: EAST-RH 7-9 Gold Image V.1.02 (HVM) 01-27-21
### EC2 Instances
Name: eAPD production
* AMI: EAST-RH 7-9 Gold Image V.1.02 (HVM) 01-27-21
* Instance type: c4.large

Name: eAPD staging
* AMI: 	EAST-RH 7-9 Gold Image V.1.02 (HVM) 01-27-21
* Instance type: c4.large

Name: eAPD PR XXXX (Temporary Instances)
* AMI: EAST-RH 7-9 Gold Image V.1.02 (HVM) 01-27-21
* Instance type: t3.medium
### Lambdas
Function Name: SSM_Failed_Association_Check
* Runtime: Python 3.7

Function Name: Assign_IAM_To_SSM_Instances
* Runtime: Python 3.7

Function Name: Assign_IAM_Role
* Runtime: Python 3.7

Function Name: CF-Custom-Resource-SSM-Association
* Runtime: Python 3.7

Function Name: eapdCloudFrontSecurityHeaders_production
* Runtime: Node.js 10.x

Function Name: Remove_Disallowed_Security_Group_Rule
* Runtime: Python 3.7

Function Name: eapdCloudFrontSecurityHeaders_staging
* Runtime: Node.js 10.x

Function Name: Check_SSM_Association_Status
* Runtime: Python 3.7

### Load Balancers
Name: eapd-staging
* Type: application
* Scheme: internet-facing

Name: eapd-staging-actual
* Type: application
* Scheme: internet-facing

### RDS
DB identifier: prod-eapd-cms-gov
* Role: Instance
* Engine: PostgreSQL 10.13
* Class: db.m3.medium

DB identifier: staging-eapd-cms-gov
* Role: Instance
* Engine: PostgreSQL 10.13
* Class: db.m3.medium
### S3 Buckets
Bucket name: 582599238767-ssm-patch-logs
* Access: Bucket and objects not public
* ACL: Our Account
* Bucket Policy: None
* CORS Config: None

Bucket name: aws-hhs-cms-cmcs-hi-c
* Access: Bucket and objects not public
* ACL: Our Account
* Bucket Policy: The block public access settings turned on for this bucket prevent granting public access.
* CORS Config: None

Bucket name: cf-templates-hi-c-v3
* Access: Objects can be public
* ACL: Our Account
* Bucket Policy: None
* CORS Config: None

Bucket name: eapd.cms.gov
* Access: Bucket and objects not public
* ACL: Our Account
* Bucket Policy: The block public access settings turned on for this bucket prevent granting public access.
* CORS Config: None

Bucket name: elb-access-logs-bucket-582599238767
* Access: Objects can be public
* ACL: Our Account
* Bucket Policy: None
* CORS Config: None

Bucket name: files.eapd.cms.gov
* Access: Bucket and objects not public
* ACL: Our Account
* Bucket Policy: None
* CORS Config: None

Bucket name: files.staging.eapd.cms.gov
* Access: Bucket and objects not public
* ACL: Our Account
* Bucket Policy: None
* CORS Config: None

Bucket name: global-account-templates-582599238767
* Access: Objects can be public
* ACL: Our Account
* Bucket Policy: None
* CORS Config: None

Bucket name: staging-eapd.cms.gov
* Access: Bucket and objects not public
* ACL: Our Account
* Bucket Policy: The block public access settings turned on for this bucket prevent granting public access.
* CORS Config: None

Bucket name: storybook.hitech.eapd.cms.gov
* Access: Public
* ACL: Our Account
* Bucket Policy: Public
* CORS Config: None
### Volumes
Name: (None)
* Volume ID: vol-075241b0e94e388da
* Size: 30 GiB
* Volume Type: gp2
* Snapshot: snap-00a89b5acf4e2222a
* Created: July 6, 2020 at 1:37:16 PM UTC-4
* State: in-use
* Attachment Information: i-051d447ed9c3434b8 (eAPD staging):/dev/sda1 (attached)

Name: (None)
* Volume ID: vol-07d6ae4e777aac6fc
* Size: 8 GiB
* Volume Type: gp2
* Snapshot: snap-062700013f593e38c
* Created: July 2, 2020 at 4:42:02 PM UTC-4
* State: in-use
* Attachment Information: i-0562c08bc36e35f9f (eAPD PR 2334):/dev/xvda (attached)

Name: (None)
* Volume ID: vol-0b9b9d82fdebcad3d
* Size: 8 GiB
* Volume Type: gp2
* Snapshot: snap-062700013f593e38c
* Created: June 30, 2020 at 4:33:36 PM UTC-4
* State: in-use
* Attachment Information: i-014caad862c0a0fa7 (eAPD PR 2315):/dev/xvda (attached)

Name: (None)
* Volume ID: vol-0edffc30a95c5dc02
* Size: 30 GiB
* Volume Type: gp2
* Snapshot: snap-00a89b5acf4e2222a
* Created: June 30, 2020 at 12:25:37 PM UTC-4
* State: in-use
* Attachment Information: i-0412f8c4be4c4dec9 (eAPD production):/dev/sda1 (attached)

Name: (None)
* Volume ID: vol-0cf2c83761b195353
* Size: 8 GiB
* Volume Type: gp2
* Snapshot: snap-062700013f593e38c
* Created: June 9, 2020 at 4:16:19 PM UTC-4
* State: in-use
* Attachment Information: i-0b62b5ec35a872f00 (eAPD PR 2285):/dev/xvda (attached)

Name: (None)
* Volume ID: vol-071d01ea4ff934f81
* Size: 8 GiB
* Volume Type: gp2
* Snapshot: snap-0ff5b79fdf9b021e8
* Created: March 13, 2019 at 4:23:20 PM UTC-4
* State: in-use
* Attachment Information: i-06fc432b409d19dab (eAPD Jumpbox):/dev/xvda (attached)
### VPC
Name: (None)
* VPC ID: vpc-2de83957
* IPv4 CIDR: 172.31.0.0/16
* Default VPC: Yes

Name: HI-C-dev-vpc
* VPC ID: vpc-00a77739f6d1c4175
* IPv4 CIDR: 10.234.218.0/23
* Default VPC: No


# Software
CircleCI (SaaS)

CodeCov (SaaS)

Docker - Generates Artifacts & Local Dev, not used in Staging or Prod

GitHub (SaaS)

PostgreSQL - 10.6
## Client Javascript modules
* axios - ^0.19.2
* axios-mock-adapter - ^1.18.1
* babel/cli - ^7.8.4
* babel/core - ^7.9.0
* babel/node - ^7.8.7
* babel/plugin-proposal-class-properties - ^7.8.3
* babel/plugin-syntax-dynamic-import - ^7.8.3
* babel/plugin-transform-runtime - ^7.9.0
* babel/polyfill - ^7.8.7
* babel/preset-env - ^7.9.0
* babel/preset-react - ^7.9.4
* babel-eslint - ^10.1.0
* babel-jest - ^24.9.0
* babel-loader - ^8.1.0
* babel-plugin-transform-require-context - ^0.1.1
* cmsgov/design-system-core - ^3.7.0
* cmsgov/design-system-layout - ^3.7.0
* connected-react-router - ^6.8.0
* css-loader - ^3.4.2
* cssnano - ^4.1.10
* d3-format - ^1.4.3
* d3-geo - ^1.11.9
* detect-browser - ^4.8.0
* enzyme - ^3.11.0
* enzyme-adapter-react-16 - ^1.15.2
* enzyme-to-json - ^3.4.4
* eslint - ^6.8.0
* eslint-config-airbnb - ^18.1.0
* eslint-config-prettier - ^6.10.1
* eslint-plugin-import - ^2.20.1
* eslint-plugin-jsx-a11y - ^6.2.3
* eslint-plugin-react - ^7.19.0
* file-loader - ^4.3.0
* fortawesome/fontawesome-svg-core - ^1.2.28
* fortawesome/free-regular-svg-icons - ^5.13.0
* fortawesome/free-solid-svg-icons - ^5.13.0
* fortawesome/react-fontawesome - ^0.1.9
* history - ^4.10.1
* html-webpack-plugin - ^3.2.0
* i18n-js - ^3.5.1
* jest - ^25.2.0
* json-loader - ^0.5.7
* jsonpatch - ^3.0.1
* js-yaml - ^3.13.1
* markdown-it - ^10.0.0
* mini-css-extract-plugin - ^0.9.0
* moment - ^2.22.2
* node-sass - ^4.14.1
* postcss - ^7.0.27
* postcss-cli - ^7.1.1
* postcss-cssnext - ^3.1.0
* postcss-custom-properties - ^9.1.1
* postcss-import - ^12.0.1
* postcss-loader - ^3.0.0
* postcss-url - ^8.0.0
* prettier - ^1.19.1
* prop-types - ^15.6.2
* react - ^16.13.1
* react-dom - ^16.13.1
* react-hot-loader - ^4.12.20
* react-redux - ^7.2.0
* react-router - ^5.1.2
* react-router-dom - ^5.1.2
* react-test-renderer - ^16.13.1
* react-waypoint - ^9.0.2
* redux  - ^4.0.5
* redux-logger - ^3.0.6
* redux-mock-store - ^1.5.4
* redux-thunk - ^2.3.0
* reselect - ^4.0.0
* resolve-url-loader - ^3.1.1
* sass-loader - ^8.0.2
* sinon - ^8.1.1
* stickybits - ^3.7.4
* style-loader - ^1.1.3
* tinymce/tinymce-react
* tinymce - ^5.2.2
* topojson - ^3.0.2
* updeep - ^1.2.0
* webpack - ^4.42.1
* webpack-cli - ^3.3.11
* webpack-dev-server - ^3.11.0
* yaml-jest - ^1.0.5
* yaml-loader - ^0.5.0
* zxcvbn - ^4.4.2

## API/Backend Javascript modules
* ajv - ^6.12.0
* aws-sdk - ^2.646.0
* axios - ^0.19.2
* body-parser - ^1.19.0
* colors - ^1.4.0
* compression - ^1.7.3
* cookies - ^0.8.0
* cors - ^2.8.5
* dotenv - ^8.2.0
* eslint - ^6.8.0
* express - ^4.17.1
* form-data - ^3.0.0
* jest - ^25.2.1
* jsonpatch - ^3.0.1
* jsonpointer - ^4.0.1
* jsonwebtoken - ^8.5.0
* knex - ^0.20.13
* moment - ^2.24.0
* multer - ^1.4.2
* node - ^10.14
* nodemon - ^2.0.2
* passport - ^0.4.1
* passport-local - ^1.0.0
* pg - ^7.18.2
* prettier - ^1.19.1
* sinon - ^8.1.1
* stream-mock - ^2.0.5
* tap - ^14.10.6
* uuid - ^3.4.0
* winston - ^2.4.4
* zxcvbn - ^4.4.2