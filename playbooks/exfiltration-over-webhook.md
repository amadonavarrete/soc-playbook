## Playbook: Exfiltration Over Webhook
    
### MITRE

| Tactic | Technique ID | Technique Name | Sub-Technique Name | Platforms | Permissions Required |
| ------ | ------------ | -------------- | ------------------ |---------- |--------------------- |
|Exfiltration|T1567.004|Exfiltration Over Web Service|Exfiltration Over Webhook|ESXi, Linux, Office Suite, SaaS, Windows, macOS|Direct access to webhook endpoint|


```
(P) Preparation

1. Monitor webhook usage.
2. Block commonly abused webhook domains and inspect DNS queries for anomalies.
3. Set up rules to detect beaconing or unusual exfiltration.
4. Deploy DLP tools to inspect outbound content for sensitive data.
5. Utilize firewalls/proxies to limit outbound HTTP/HTTPS to approved domains/IPs.
6. Disable script execution where necessary.
7. Never hardcode webhook URLs in scripts or code repositories.
8. Educate developers and users on the risk of exposing webhooks and how to secure them.
 
```
  
Assign steps to individuals or teams to work concurrently, when possible; this playbook is not purely sequential. Use your best judgment.

--------------

### Investigate

#### Key Questions
- What process or user initiated the webhook request?
- What type of data was transmitted and to which external service?
- Has this behavior occurred elsewhere in the environment?

1. Search for outbound HTTP/HTTPS `POST` requests to webhook-related domains.
2. Check browser history, shell history, and running processes.
3. Review PCAPs/proxy logs for data patterns and frequency.
4. Inspect any scripts, binaries, or files that generated the traffic.
5. Look for similar indicators across peer systems.

--------------

### Remediate

* **Plan remediation events** where these steps are launched together (or in coordinated fashion), with appropriate teams ready to respond to any disruption.
* **Consider the timing and tradeoffs** of remediation actions: your response has consequences.

#### Contain

1. **Isolate the affected host**
   - **Procedure**: Immediately quarantine the host to prevent further exfiltration or lateral movement.
   - **Automate**: Utilize SOAR to auto-isolate based on IOC or alert severity.
   - **Tools**: `EDR/XDR platforms`
2. **Block outbound webhook domains/IPs**
   - **Procedure**: Add known malicious webhook URLs or IPs to blocklists.
   - **Automate**: Trigger dynamic rule updates via threat intelligence feeds and orchestration playbooks.
   - **Tools**: `Firewall, Web Proxy, DNS Filtering`
4. **Revoke webhook access (if internal)**
   - **Procedure**: Invalidate or delete exposed webhook URLs and rotate any associated secrets.
   - **Automate**: Use scripted API calls to disable webhooks upon detection.
   - **Tools**: `API Management Portals, DevOps Tools`

#### Eradicate

1. **Remove malicious artifacts**
   - **Procedure**: Scan and remove malicious scripts, binaries, or scheduled tasks used for webhook-based exfiltration.
   - **Tools**: `EDR/AV platforms`
2. **Disable compromised accounts or credentials**
   - **Procedure**: Disable or reset accounts involved in the compromise, especially if credentials were used to access webhook endpoints.
   - **Tools**: `IAM/IDP`
3. **Clear persistence mechanisms**
   - **Procedure**: Identify and remove persistence techniques such as startup entries, scheduled tasks, or registry changes.
   - **Tools**: `Sysinternals, EDR platforms`
4. **Reimage if necessary**
   - **Procedure**: If system integrity is questionable, initiate a secure reimage of the affected asset.
   - **Tools**: `Endpoint management systems`

--------------

### Communicate

*Refer to organization's Incident Response Communication Plan for escalation matrix, timing, and format.*

--------------

### Recover

`TODO: Customize recovery steps for <Type of Incident>.`

`TODO: Specify tools and procedures for each step, below.`

In addition to the general steps and guidance in the incident response plan:


--------------
  
### Lessons Learned

The goal of the phase is to discover how to improve the incident response process.  
You need to answer some basic questions, using developed incident report:  

- What happened?  
- What did we do well?  
- What could we have done better?  
- What will we do differently next time?  

The incident report is the key to improvements.  

`TODO: Add items that will occur post recover.`
  
1.    Perform routine cyber hygiene due diligence
2.    Engage external cybersecurity-as-a-service providers and response professionals
 

##### Develop the incident report

Develop the Incident Report using your corporate template.  

It should include:  

1. Executive Summary with a short description of damage, actions taken, root cause, and key metrics (Time To Detect, Time To Respond, Time To Recover etc)  
2. Detailed timeline of adversary actions mapped to [ATT&CK tactics](https://attack.mitre.org/tactics/enterprise/), but most probably most of the actions will be in Actions On Objective stage, which is not very representative and useful)  
3. Detailed timeline of actions taken by Incident Response Team  
4. Root Cause Analysis and Recommendations for improvements based on its conclusion  
5. List of specialists involved in Incident Response with their roles  

 

--------------

### Resources

#### Additional Information

1. Playbook template adapted from [Incident-Playbook by austinsonger](https://github.com/austinsonger/Incident-Playbook), licensed under the MIT License.
2. <a name="identity-and-access-playbook-ref-1"></a>["Title"](#TODO-url), Author Last Name (Date)


