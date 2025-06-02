# Database Recovery Plan - DRAFT

You can restore a DB instance to a specific point in time, creating a new DB instance. When you restore a DB instance to a point in time, the default DB security group is applied to the new DB instance. If you need custom DB security groups applied to your DB instance, you must apply them explicitly.

RDS uploads transaction logs for DB instances to Amazon S3 every 5 minutes. To determine the latest restorable time for a DB instance, use the AWS CLI describe-db-instances command and look at the value returned in the LatestRestorableTime field for the DB instance.

`aws rds describe-db-instances`

## Console
### To restore a DB instance to a specified time

1. Sign in to the AWS Management Console and open the Amazon RDS console at https://console.aws.amazon.com/rds/.

2. In the navigation pane, choose Databases.

3. Choose the DB instance that you want to restore.

4. For Actions, choose Restore to point in time.
The Launch DB Instance window appears.

5. Choose Latest restorable time to restore to the latest possible time, or choose Custom to choose a time.

If you chose Custom, enter the date and time that you want to restore the instance to.

Note
Times are shown in your local time zone, which is indicated by an offset from Coordinated Universal Time (UTC). For example, UTC-5 is Eastern Standard Time/Central Daylight Time.

6. For DB instance identifier, enter the name of the target restored DB instance.

7. Choose other options as needed.

8. Choose Launch DB Instance.

## AWS CLI
To restore a DB instance to a specified time, use the AWS CLI command restore-db-instance-to-point-in-time to create a new DB instance.

For Linux, macOS, or Unix:

`aws rds restore-db-instance-to-point-in-time \`
    `--source-db-instance-identifier mysourcedbinstance \`
    `--target-db-instance-identifier mytargetdbinstance \`
    `--restore-time 2017-10-14T23:45:00.000Z`

For Windows:

`aws rds restore-db-instance-to-point-in-time ^`
    `--source-db-instance-identifier mysourcedbinstance ^`
    `--target-db-instance-identifier mytargetdbinstance ^`
    `--restore-time 2017-10-14T23:45:00.000Z`

https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PIT.html

## Backup
### Prod
Automated backups: Enabled (7 Days)
Copy tags to snapshots: Enabled
VPC security groups: HiC-database-sg (sg-02161621997e5ad37), eAPD Production RDS (sg-0e8ec17f26d3bb4c9)


### Staging
Automated backups: Enabled (7 Days)
Copy tags to snapshots: Disabled
VPC security groups: eAPD Staging RDS (sg-0a6b8b834c21c0995)


## Time to Restored (Ideal Conditions from Exercise):
Start: 10:00 am
DB Created: 10:20 am
Update & Run CircleCI Ended: 10:40 am
Put everything back in place: 10:40 am
End: 11:08 am

## Steps to restore via AWS Console
1. Log into AWS Console
2. Navigate to RDS >> Databases
3. Select the Database to be restored from Snapshot
4. From the “Actions” dropdown select “Restore to point in time”
5. Select “Latest restorable time” or use the “Custom” option to select the last known good database restore point

Leave the default values unless otherwise specified

6. “DB instance identifier” must be different from the name of the database you are restoring. I suggest something like: staging-eapd-cms-gov-20201008 (year/month/day)
7. “Availability & durability” staging does not require any changes here, production will you to click the “Create a standby instance” radial
8. Lastly click “Launch DB Instance”

9. Log Into CircleCI
10. Take note of the endpoint URL (in the AWS console) of the new database (once it populates towards the end of creation)
10a. This can be found by going back to the “Databases” section
10b. Clicking on the database
10c. Finding the “Endpoint” section in the “Connectivity & Security” tab
11. Replace the existing URL section of the STAGING_API_DATABASE_URL variable with the new endpoint URL (ex postgres://username:password@newendpointurl/database) in the CircleCI “Environment Variables” 
12. Rerun the last CircleCI deploy to staging/production (depending on the database you are restoring)
13. Once the job completes STOP the original database
14. Once the database has stopped, check the site by logging in
15. Once logged in terminate the replaced database
16. Update the environment variables in Keybase
