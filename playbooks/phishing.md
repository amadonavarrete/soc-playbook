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
   - **Procedure:** Disable or lock compromised user accounts to prevent further access.
   - **Automate:** Utilize SOAR or identity management workflows to auto-disable accounts when phishing is confirmed.
   - **Tools:** `Active Directory`
2. **Quarantine or remove malicious email**
   - **Procedure:** Search for and retract the phishing email across all user mailboxes.
   - **Automate:** Integrate with SOAR or mail security APIs to auto-quarantine emails based on IOC matches.
3. **Block malicious URLs and Domains**
   - **Procedure:** Add phishing URLs/domains to denylists at the firewall, DNS, or secure web gateway level.
   - **Automate:** Automate IOC ingestion into blocklists via threat intelligence or SOAR pipelines.
4. **Contain endpoint activity**
   - **Procedure:** Isolate or restrict network access for affected endpoints.
   - **Automate:** Configure endpoint policies to auto-isolate machines flagged for phishing payload execution or suspicious behavior.

#### Eradicate

1. **Remove persistence mechanisms (if established)**
   - **Procedure:** Scan for and remove registry entries, scheduled tasks, or startup items added by phishing payloads. 
   - **Automate:** Configure EDR or SOAR workflows to detect and automatically clean known persistence artifacts.
   - **Tools:** `EDR Platforms`
2. **Revoke compromised credentials and issue new ones**
   - **Procedure:** Reset passwords or deactivate accounts involved in credential theft. Monitor for reuse of old credentials.
   - **Automate:** Use identity orchestration to enforce password resets and monitor credential reuse attempts.
   - **Tools:** `Active Directory`
3. **Clear malicious artifacts from infected systems**
   - **Procedure:** Perform full endpoint scans and remove malicious files, scripts, or executables delivered via phishing.
   - **Automate:** Trigger full endpoint scans via EDR or SOAR playbook when phishing indicators are confirmed.
4. **Remove malicious email rules or forwarding settings**
   - **Procedure:** Check and delete any unauthorized mailbox rules that forward emails or auto-delete messages.
   - **Automate:** Use scripting or SOAR integrations to identify and clean rules in bulk.
5. **Purge residual phishing emails**
   - **Procedure:** Search and purge any remaining instances of the phishing email from user mailboxes.
   - **Automate:** Automate email purging via API calls from mail security solutions when malicious indicators are confirmed.

--------------

### Communicate

*Refer to organization's Incident Response Communication Plan for escalation matrix, timing, and format.*

--------------

### Recover

In addition to the general steps and guidance in the incident response plan:

1. **Restore affected systems to trusted state**
   - **Procedure:** Reimage compromised endpoints or restore from known-good backups to ensure removal of phishing-related malware.
   - **Tools:** `Endpoint management platforms, backup solutions`
2. **Re-enable user accounts with updated credentials**
   - **Procedure:** After confirming no ongoing compromise, reinstate affected accounts with enforced password changes and MFA validation.
   - **Tools:** `Active Directory`
3. **Validate system integrity and functionality**
   - **Procedure:** Perform post-restoration checks, including log reviews and endpoint scans, to verify clean state and operational readiness.
   - **Tools:** `EDR Tools, system health monitors`
4. **Monitor for recurrence or residual indicators**
   - **Procedure:** Maintain increased monitoring of involved accounts, endpoints, and domains for a defined period.
   - **Tools:** `SIEM, EDR dashboards`
5. **Document recovery actions and update incident ticket**
   - **Procedure:** Record all recovery steps, outcomes, and verification details to close out the incident formally.
   - **Tools:** `Internal incident response documentation systems`


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
- **Reference:** [MITRE ATT&CK T1566 - Phishing](https://attack.mitre.org/techniques/T1566/)
- **Playbook Owner:** Amado | Created May 2025


