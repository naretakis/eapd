# Mongo Recovery Plan - DRAFT

You can restore a Mongo EC2 Instance to a specific point in time, creating a new Mongo EC2 Instance. When you restore a Mongo EC2 Instance to a point in time, the Mongo security groups is applied to the new Mongo EC2 Instance. If you need custom security groups applied to your instance, you must apply them explicitly.

CPM creates Mongo EC2 Instance every 4 hours. To determine the latest restorable time for a Mongo EC2 Instance, use either the CPM Interface (requires VPN and credentials/job codes) or AWS > EC2 > Elastic Block Store > Snapshots and sort by "Started."

Required Staging Mongo Security Groups
```
sg-0f83d0cfcb25583e5 - eapd-staging-mongo-ec2
sg-01e01435dbbe6ce32 - eAPD Staging EC2
```

Required Production Mongo Security Groups
```
sg-0adaea3ae0dde6b04 - eapd-production-mongo-ec2
sg-01e01435dbbe6ce32 - eAPD Staging EC2
```

## Security Group Rules
eapd-environment-mongo-ec2
| Descriptions | Type | Protocol | Port Range | Source | 
| :------------|:-----|:---------|:-----------|:-------|
| Mongo Traffic from Production Instance | Custom TCP | TCP | Mongo Ports | SG ID for eAPD Environment EC2 |
| Mongo Traffic from Jumpbox | Custom TCP | TCP | Mongo Ports | SG ID for VPN |
| SSH Access from Jumpbox | SSH | TCP | SSH Port | 

eAPD Environment EC2
| Descriptions | Type | Protocol | Port Range | Source | 
| :------------|:-----|:---------|:-----------|:-------|
|   | SSH | TCP | SSH Port | SG ID for VPN |
| API HTTP listener | Custom TCP | TCP | API HTTP Listener Port | 

## Console
### To restore a Mongo EC2 Instance to a specified time

1. Sign in to the AWS Management Console and open the Amazon EC2 console at https://console.aws.amazon.com/ec2/.

2. In the navigation pane, choose Elastic Block Store > Snapshots.

3. Choose the Snapshot that you want to restore.

4. From Actions, choose "Create volume from snapshot".
The "Create volume" window appears.

5. Create the new volume in the same Availability Zone as your EC2 instance.

6. On the Amazon EC2 console, select the instance.

7. In the instance details, make note of the device name that you want to replace in the Root device entry or Block Devices entries.

8. Attach the volume. The process differs for root volumes and non-root volumes.

  For root volumes:

  a. Stop the EC2 instance.

  b. On the EC2 Elastic Block Store Volumes menu, select the root volume that you want to replace.

  c. Choose Actions, and then choose Detach Volume.

  d. On the EC2 Elastic Block Store Volumes menu, select the new volume.

  e. Choose Actions, and then choose Attach Volume.

  f. Select the instance that you want to attach the volume to, and use the same device name that you noted earlier.

  For non-root volumes:

  a. On the EC2 Elastic Block Store Volumes menu, select the non-root volume that you want to replace.

  b. Choose Actions, and then choose Detach Volume.

  c. Attach the new volume by choosing it on the EC2 Elastic Block Store Volumes menu and then choosing Actions, Attach Volume. Select the instance that you want to attach it to, and then select an available device name.

  d. Using the operating system for the instance, unmount the existing volume, and then mount the new volume in its place.

  In Linux, you can use the umount command. In Windows, you can use a logical volume manager (LVM) such as the Disk Management system utility.

  e. Detach any prior volumes that you may be replacing by choosing it on the EC2 Elastic Block Store Volumes menu and then choosing Actions, Detach Volume.

You can also use the AWS CLI in combination with operating system commands to automate these steps.

If the IP address of the Mongo EC2 Instance has changed update the Mongo environment variables in CircleCI and Keybase and redeploy the respective backend instance.
