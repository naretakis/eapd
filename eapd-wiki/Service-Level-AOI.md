# Service Level [AOI] - DRAFT
## Service Level Objectives

### External
http://eapd.cms.gov/ is available 99.9% of the year ( all but ~8 hours)
a. 2 hours for major infrastructure upgrades that are cost-prohibitive to blue green
b. 6 hours per year for AWS outages and other management reserve
c. Site fully loads in < 5 seconds

## Service Level Indicators
The primary goal here is to define indicators (metrics) that are useful and actionable. MACPro eAPD’s mission is to support the states creation, submission, and response process for APDs and contracts.

In order to support the states, the system needs to be available and responding in a reasonable amount of time.  As such, the most important primary indicators will be the ratio of successful responses and the latency in those responses. All other indicators can help indicate or predict other deeper issues, but do not directly indicate the ability to serve information.

As such, monitoring efforts should focus on:
1. Availability Monitoring
2. Rate of HTTP 400/500 responses from the ELB
3. Duration of HTTP 200 responses ELB Targets

Indicators that are generally NOT useful for availability monitoring, but may help with troubleshooting, proper provisioning and configuration changes:
1. CPU usage
2. Memory Usage

(High levels of CPU and memory usages generally indicate proper provisioning of resources and therefore should be carefully considering when investigating a reported issue)

### Availability
Endpoint | Service | Status | Alert 
---------|---------|--------|-------
https://eapd.cms.gov/ | Primary | Not Available | Alert

### Health
Service | Metric | Stat | Period | Threshold | # of Datapoints | Actions | Notes
--------|--------|------|--------|-----------|-----------------|---------|------
Application ELB | HTTPCode_Target_5XX_Count | Average | 5 minutes | > 200 | 2 | Alert | 
| | HTTPCode_Target_5XX_Count | Average | 5 minutes | > 50 | 5 | Warn | 
| | TargetResponseTime | p95 | 5 minutes | > 2.5 seconds | 2 | Alert | 
| | TargetResponseTime | p95 | 5 minutes | > 0.5 seconds | 5 | Warn | 
Instances | HealthyHostCount | Average | 5 | 1 | 1 | Alert | 
| | CPUUtilization | n/a | n/a | < 20% | n/a | Alert | 
RDS | CPUUtilization | Average | 5 | > 50% | 2 | Warn | 
Lambdas | Errors | n/a | n/a | > 0 | n/a | Alert | 

* Alerts would trigger an alerting mechanism for investigation by on-call
* Warning would generate a report that should be investigated
