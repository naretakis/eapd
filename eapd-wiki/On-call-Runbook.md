## On-call Checklist
### Routine Duties
- [ ] On-call is available during hours of operation
- [ ] On-call is monitoring Slack cmcs-dsg-eapd-alerts/notifications
- [ ] On-call will find a substitute if they are unable to cover and update the Availability Calendar
- [ ] On-call will respond/reply to Slack UnHealthyHostCount Alert
- [ ] On-call will respond/reply to TargetResponseTime Alert  
Note: Please reply to the alert, it provides time stamp data that emotes on the alert do not


### Incident Response
- [ ] On-call assess alert and declares an incident
- [ ] On-call will either become the incident command or the subject matter expert and will tap someone to fill the role they are not filling
- [ ] On-call IF subject matter expert, will work the incident
- [ ] On-call IF Incident Commander, will create Incident Response Document
- [ ] On-call IF Incident Commander, will update eapd-user-support  
Example:  
```
:construction:  SYSTEM OUTAGE  :construction:
The eAPD system is currently unavailable. We apologize for this inconvenience. We will post an update when the system is available again.
```

### Investigating Alerts
- [ ] Visit the site; eapd.cms.gov/ or staging-eapd.cms.gov/
- [ ] If the site is working attempt to log in
- [ ] If you can log in try to navigate the site
- [ ] If site doesn't load check your browsers web dev tools for errors
- [ ] Log into AWS and look at CloudWatch logs; prefix production/ for Prod, prefix staging/ for Staging, bonus fact: prefix preview/ for Preview

## Resources:
https://github.com/Enterprise-CMCS/eAPD/wiki/On-Call-Policy  
https://github.com/Enterprise-CMCS/eAPD/wiki/Infrastructure-Contingency-Plan  
https://github.com/Enterprise-CMCS/eAPD/wiki/Database-Recovery-Plan  
https://github.com/Enterprise-CMCS/eAPD/wiki/Emergency-Deploy-to-Staging-Runbook  
https://github.com/Enterprise-CMCS/eAPD/wiki/Mongo-Recovery-Plan  