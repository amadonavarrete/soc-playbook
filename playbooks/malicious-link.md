## Playbook: Malicious Link  
  
### MITRE

| Tactic | Technique ID | Technique Name | Sub-Technique Name | Platforms | Permissions Required |
| ------ | ------------ | -------------- | ------------------ |---------- |--------------------- |
|Execution|T1204.001    |User Execution  |Malicious Link      |Linux, Windows, macOS|Access to delivery channel, user interaction, and outbound network access from the host|


```
(P) Preparation

1. Implement URL filtering and DNS protections.
2. Enforce least privilege on endpoints.
3. Enable security features in browsers.
4. Preconfigure incident response tools.
5. Conduct user awareness training.
6. Maintain threat intelligence feeds.
 
```
  
Assign steps to individuals or teams to work concurrently, when possible; this playbook is not purely sequential. Use your best judgment.

--------------

### Investigate

#### Key Questions
- **Did the user click the link, and what was the result?**
- **What endpoint/network activity occurred immediately after the link was accessed?**
- **Was any payload delivered, and if so, was it executed or blocked?**

1. Identify the user and system involved.
2. Analyze the link and destination.
3. Review endpoint activity.
4. Check network traffic.
5. Look for indicators such as new executables, scripts, or persistence mechanisms.
6. Investigate whether other users received or clicked the same link.
7. Identify potential lateral movement or privilege escalation stemming from the initial event.

--------------

### Remediate

* **Plan remediation events** where these steps are launched together (or in coordinated fashion), with appropriate teams ready to respond to any disruption.
* **Consider the timing and tradeoffs** of remediation actions: your response has consequences.

#### Contain

1. **Isolate the affected endpoint**
   - Restrict all outbound/inbound communications immediately.
2. **Quarantine downloaded files**
   - Locate and isolate any files downloaded as a result of the link click.
3. **Block malicious domains/IPs**
4. **Disable affected user accounts temporarily (if compromise suspected)**
   - Suspend the user's account to prevent further malicious activity.
   - Monitor for attempts to reauthenticate.
5. **Alert and engage SOC Tier 2 or IR Team**

  
#### Eradicate

1. **Remove malicious files and artifacts**
   - Identify and delete any malicious files, scripts, registry entries, or scheduled tasks.
2. **Reimage or deep clean infected systems**
   - Fully reimage compromised systems or conduct deep scans to remove persistent threats.
3. **Revoke or reset compromised credentials**
   - Invalidate any user credentials that may have been harvested and enforce password resets.
   - Check for reuse of credentials across other systems and rotate if necessary.
4. **Purge malicious emails or messages**
5. **Update blocklists and detection rules**
--------------

### Communicate

*Refer to organization's Incident Response Communication Plan for escalation matrix, timing, and format.*  

--------------

### Recover

In addition to the general steps and guidance in the incident response plan:

1. **Restore affected systems from clean backups**
   - Use verified, malware-free backups to restore compromised endpoints.
2. **Re-enable user accounts and access**
   - Once confidence is established that no compromise persists, re-enable any disabled user accounts and confirm multifactor authentication is enforced.
3. **Validate email system integrity**
   - Conduct a post-incident review of mail flow and delivery settings.
4. **Conduct post-restoration testing**
   - Run vulnerability scans and endpoint health checks to confirm no residual threats remain and that systems are operating normally.

--------------
  
### Lessons Learned

1.  Identify delays, missteps, or coordination issues in detection, containment, or escalation.
2.  Integrate new indicators and refine rules to improve future alerting.
3.  Address user behavior that led to the incident (reinforce safe link-handling practices).
4.  Adjust containment and remediation actions based on what worked and what didn't.
5.  Document findings and assign follow-up actions.

 

--------------

### Resources

#### Additional Information

- Playbook template adapted from [Incident-Playbook by austinsonger](https://github.com/austinsonger/Incident-Playbook), licensed under the MIT License.


