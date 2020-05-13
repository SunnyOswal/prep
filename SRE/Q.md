# Availability vs Reliability
+ **Availability**: percentage of time that the infrastructure, system or a solution remains operational under normal circumstances in order to serve its intended purpose.  
    + The measurement of Availability is driven by time loss
    + **Percentage of availability** = (total elapsed time – sum of downtime)/total elapsed time
+ **Reliability**:
probability that the system will meet certain performance standards in yielding correct output for a desired time duration.  
    + The measurement of Reliability is driven by the frequency and impact of failures.
    
# High Availability can be achieved by ?
+ Prefer regional deploys over global ones
+ Use Blue/Green deployment strategy for production deploys
+ Use deployment windows
+ Ensure automatically triggered deploys are not executed during off-hours or weekends
+ Enable [Chaos Monkey](https://github.com/netflix/chaosmonkey): resiliency tool that helps applications tolerate random instance failures
+ Use (unit, integration, smoke) testing and canary analysis to validate code before it is pushed to production
+ Automate where possible, but use manual intervention where appropriate.
+ Where possible, deploy exactly what you tested to production
+ Regularly Review paging settings
+ Know how to roll back your deploy quickly
+ Fail a deployment when instances are not coming up healthy
+ For automated deployments, notify the team of impending and completed deployments
+ Automate non-typical deployment situations rather than doing one-off manual work
+ Use preconditions to verify expected state

# SLA , SLI & SLO  
It’s always better to under-promise and overdeliver.  

+ **Service Level Agreement** : agreement between provider and client about measurable metrics like uptime, responsiveness, and responsibilities. 
+ **Service Level Indicator** : measures compliance with an SLO (service level objective).  
    + If your SLA specifies that your systems will be available 99.95% of the time, your SLO is likely 99.95% uptime and your SLI is the actual measurement of your uptime. Maybe it’s 99.96%. Maybe 99.99%.  
    + To stay in compliance with your SLA, the SLI will need to meet or exceed the promises made in that document.
    + Examples:
         + No. of successful HTTP calls/No. of HTTP calls at the LB
         + No. of operations that completed in < 10ms/No. of operations at the client
         + No. of “full quality responses”/No. of responses in the server log
         + No. of records processed/No. of records as determined by the app
+ **Service Level Objective** : agreement within an SLA about a specific metric like uptime or response time. 
    + So, if the SLA is the formal agreement between you and your customer, SLOs are the individual promises you’re making to that customer. 
    + SLOs are what set customer expectations and tell IT and DevOps teams what goals they need to hit and measure themselves against.

![ServiceLevel](https://github.com/SunnyOswal/prep/blob/master/images/ServiceLevel.PNG)
![ServiceLevelGoals](https://github.com/SunnyOswal/prep/blob/master/images/ServiceLevelGoals.PNG)
