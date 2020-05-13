# Availability vs Reliability
+ **Availability**: percentage of time that the infrastructure, system or a solution remains operational under normal circumstances in order to serve its intended purpose.  
    + The measurement of Availability is driven by time loss
    + **Percentage of availability** = (total elapsed time – sum of downtime)/total elapsed time
+ **Reliability**:
probability that the system will meet certain performance standards in yielding correct output for a desired time duration.  
    + The measurement of Reliability is driven by the frequency and impact of failures.
    
# SLA , SLI & SLO
+ **SLA**:
    + **Service Level Agreement** : agreement between provider and client about measurable metrics like uptime, responsiveness, and responsibilities. 
+ **SLI**:
    + **Service Level Indicator** : measures compliance with an SLO (service level objective).  
        + If your SLA specifies that your systems will be available 99.95% of the time, your SLO is likely 99.95% uptime and your SLI is the actual measurement of your uptime. Maybe it’s 99.96%. Maybe 99.99%.  \
        + To stay in compliance with your SLA, the SLI will need to meet or exceed the promises made in that document.
+ **SLO**:
    + **Service Level Objective** : agreement within an SLA about a specific metric like uptime or response time. 
        + So, if the SLA is the formal agreement between you and your customer, SLOs are the individual promises you’re making to that customer. 
        + SLOs are what set customer expectations and tell IT and DevOps teams what goals they need to hit and measure themselves against.

![ServiceLevel](https://github.com/SunnyOswal/prep/blob/master/images/ServiceLevel.PNG)
![ServiceLevelGoals](https://github.com/SunnyOswal/prep/blob/master/images/ServiceLevelGoals.PNG)
