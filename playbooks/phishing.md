## Playbook: Phishing

### MITRE

| Tactic | Technique ID | Technique Name | Platforms | Permissions Required |
| ------ | ------------ | -------------- | ---------- |--------------------- |
|Initial Access|T1566   |Phishing        | Identity Provider, Linux, Office Suite, SaaS, Windows, macOS|Access to email inbox or delivery channel|


```
(P) Preparation

1. Conduct user awareness training.
2. Implement email security tools.
3. Establish incident reporting channels.
4. Enable MFA.
5. Preconfigure detection rules.
6. Maintain threat intelligence feeds.
7. Run simulated phishing campaigns.
8. Establish response playbooks.
 
```
  
Assign steps to individuals or teams to work concurrently, when possible; this playbook is not purely sequential. Use your best judgment.

--------------

### Investigate

#### Key Questions
- **Was the user tricked into clicking a link, opening an attachment, or entering credentials?**
- **What systems, accounts, or data may have been accessed as a result?**
- **Are there indicators that similar phishing emails were delivered to other users?**

1. Secure a copy of the reported email with full headers and metadata.
2. Review sender address, domain reputation, links, attachments, and header anomalies.
3. Determine if the recipient clicked links, opened attachments, or submitted credentials.
4. Use EDR tools to review activity on the user's system.
5. Check for unusual login attempts or location mismatches after the phishing timestamp.
6. Identify whether the phishing email reached other users across the environment.
7. Pull URLs, domains, file hashes, and IPs for analysis.
8. Investigate external communications to known or suspicious phishing infrastructure.
9. Identify any additional compromised accounts or lateral movement stemming from the phishing attempt.
10. Compile investigation results for response planning and handoff to containment/remediation teams.

--------------

### Remediate

* **Plan remediation events** where these steps are launched together (or in coordinated fashion), with appropriate teams ready to respond to any disruption.
* **Consider the timing and tradeoffs** of remediation actions: your response has consequences.

#### Contain

1. **Isolate affected user accounts**
   - Disable or lock compromised accounts to prevent unauthorized access.
2. **Quarantine or remove malicious email**
   - Search for and retract the phishing email across all user mailboxes.
3. **Block malicious URLs and Domains**
   - Add phishing URLs/domains to denylists at the firewall, DNS, or secure web gateway level.
4. **Contain endpoint activity**
   - Isolate or restrict network access for affected endpoints.
   - Monitor for any additional malicious activity from the system.

#### Eradicate

1. **Remove persistence mechanisms (if established)**
   - Scan for and remove registry entries, scheduled tasks, or startup items added by phishing payloads.
2. **Revoke compromised credentials and issue new ones**
   - Reset passwords or deactivate accounts involved in credential theft.
   - Monitor for reuse of old credentials.
3. **Clear malicious artifacts from infected systems**
   - Perform full endpoint scans and remove malicious files, scripts, or executables delivered via phishing.
4. **Remove malicious email rules or forwarding settings**
   - Check and delete any unauthorized mailbox rules that forward emails or auto-delete messages.
5. **Purge residual phishing emails**
   - Search and purge any remaining instances of the phishing email from user mailboxes.

--------------

### Communicate

*Refer to organization's Incident Response Communication Plan for escalation matrix, timing, and format.*

--------------

### Recover

In addition to the general steps and guidance in the incident response plan:

1. **Restore affected systems to trusted state**
   - Reimage compromised endpoints or restore from known-good backups to ensure removal of phishing-related malware.
2. **Re-enable user accounts with updated credentials**
   - After confirming no ongoing compromise, reinstate affected accounts with enforced password changes and MFA validation.
3. **Validate system integrity and functionality**
   - Perform post-restoration checks, including log reviews and endpoint scans, to verify clean state and operational readiness.
   - Conduct basic functionality tests to confirm no service disruptions remain.
4. **Monitor for recurrence or residual indicators**
   - Maintain increased monitoring of involved accounts, endpoints, and domains for a defined period.
5. **Document recovery actions and update incident ticket**
   - Record all recovery steps, outcomes, and verification details to close out the incident formally.
   - Ensure documentation is reviewed and approved by the IR team or SOC lead.


--------------
  
### Lessons Learned

 1. Conduct a post-incident review.
 2. Identify gaps in detection and response.
 3. Update playbooks and response procedures.
 4. Enhance user awareness training.
 5. Implement control improvements.
 6. Review and test automation workflows.
 7. Document metrics and report to leadership.

--------------

### Resources

#### Additional Information

- Playbook template adapted from [Incident-Playbook by austinsonger](https://github.com/austinsonger/Incident-Playbook), licensed under the MIT License.


