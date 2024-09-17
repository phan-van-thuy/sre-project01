# Project: Deploying System Observability

## Categorizing Responsibilities
### 1. Identify SRE roles and responsibilities for hotfix release
For a hotfix release, the main SRE roles and responsibilities revolve around quickly ensuring stability and reliability while minimizing downtime.

Release Manager: This role ensures the coordination of the hotfix deployment, making sure the fix is rolled out in a controlled manner and that it doesn’t introduce new issues. They also track the release status and communicate with stakeholders.

Monitoring Engineer: This role involves actively monitoring the system before, during, and after the hotfix release to ensure no unintended side effects. The engineer sets up alerts for any unexpected behavior and works on troubleshooting issues if something goes wrong during the hotfix.

### 2. Identify SRE roles and responsibilities in new product build
For a new product build, the focus shifts toward ensuring that the product is built with reliability, scalability, and performance in mind from the start.

Infrastructure Engineer: This role is responsible for setting up the necessary infrastructure for the new product. They ensure that the infrastructure is scalable and can handle the expected load. They also take care of automation, load balancing, and redundancy.

Reliability Engineer: This role ensures that reliability is built into the product from the start. They set up error budgets, service level objectives (SLOs), and service level agreements (SLAs). They also focus on building resilience into the product by preparing for failures and planning for chaos engineering.

### 3. Identify SRE roles and responsibilities in mitigating production issues
In production issues, the key SRE roles involve fast identification, mitigation, and prevention of future occurrences.

Incident Response Engineer: This role takes immediate ownership during production incidents. They work to identify the root cause, mitigate the issue, and bring the system back to normal operation as quickly as possible. This role also involves coordinating with other teams for incident resolution and conducting post-mortems to prevent recurrence.
In all these cases, SREs ensure that services remain reliable, scalable, and efficient across various stages of software development and operation.


## Team Formation & Workflow Identification
Images for implementing requirements are saved in the "Pictures" folder.


## Applying the Concepts

### Identify API health based on dashboard
From image API Testing.png 
As we can see, the API endpoint reports down when disconnecting from the backend immediately, but the alert manager is set to wait 30 seconds to respond to the alert. Once the backend connection is restored, grafana monitoring shows that the API is up again.
API disruption will impact customers such as:
    + Disruption in Services: Customers might experience downtime or degraded performance in applications relying on the infrastructure that’s down. This could include inaccessible websites, inability to log in, or slow processing times.
    + Data Unavailability: If data storage or database services are impacted, customers may not be able to access or retrieve their data, leading to operational disruptions.
    + Delayed Transactions: E-commerce platforms or financial services might see failed or delayed transactions, which could result in customer frustration or loss of business opportunities.
    + User Experience Impact: Depending on the nature of the outage, the overall user experience would deteriorate, affecting trust and satisfaction, leading to potential churn.
Tool or Service to Alert the SRE Team:
    + Prometheus with Alertmanager: If using Kubernetes, Prometheus along with Alertmanager can be configured to send notifications based on custom alert rules.
    + New Relic or Datadog: These monitoring services can be configured to send alerts to the SRE team whenever there are performance anomalies or outages in services.

### Interpret host metric dashboard and identify associated SRE roles
Based on the NETWORK TRAFFIC.png image, we see that the network traffic of the ec2 instance (node_exporter) is using 20kb/s. With stable network traffic, the SRE team will feel secure about this, this proves that the website is operating stably and does not generate any unusual traffic.
