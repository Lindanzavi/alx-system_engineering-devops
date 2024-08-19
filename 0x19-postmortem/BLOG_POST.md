SUMMARY
Impact : 80% of the users were unable to access or use the main web application.
Affected users , experienced server errors (502 bad gateway , total unavailability and prolonged loading.
It impacted critical user workflows including , login and content submission.
ROOT CAUSE.
Misconfigured Nginx load balancer, which resulted to traffic being directed to unhealthy backend servers.
TIMELIMES
12:00 EAT:  Issue is detected by automated monitoring alerts.
12:04 EAT: Engineers begin debugging process of finding affected service. First suspecting backend database issue due recent query optimizations.
12:15 EAT:  initial check on database shows no abnormalities . The investigation then shifted to the application servers.
12:30 EAT: the issue is the escalated to the DevOps team due to unusual traffic is detected in the Nginx logs.
12:40 EAT : misleading path. Engineers assumed high traffic was the cause and attempted to scale the application horizontally .
12:50 EAT: shortly after ,the DevOps team discover that the Nginx configuration was not properly updated in the recent deployment , causing routine problems.
12:52 EAT: Nginx configuration was rolled back to the previous stable version .
12:57 EAT: servers gradually recover.
13:00 EAT: full restoration confirmed across the system. All servers return to normal.
Root cause was the faulty configuration in the Nginx load balancer . This was rectified by rolling the Nginx configuration to the previous working version.
CORRECTIVE AND PREVENTIVE MEASURES 
AREAS OF IMPROVEMENT 
Deployment process—refine the deployment process.
Configuration testing—improve pre-deployment testing of load balancer configuration to catch such issues earlier .
Monitoring enhancements .
TASKS
Implement automated Nginx configuration tests in CI/CD pipeline to ensure syntax and routing logic are in place before deployment.
A healthy check to monitor the status of upstream servers after every deployment to avoid unhealthy servers receiving traffic.
Update deployment scripts to have an automated rollback  trigger if system health degrades in 15minutes.

