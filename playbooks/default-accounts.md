## Playbook: Default Accounts
  
### MITRE

| Tactic | Technique ID | Technique Name | Sub-Technique Name | Platforms | Permissions Required |
| ------ | ------------ | -------------- | ------------------ |---------- |--------------------- |
|Defense Evasion, Persistence, Privilege Escalation, Initial Access|T1078.001|Valid Accounts|Default Accounts|Containers, ESXi, IaaS, Identity Provider, Linux, Network Devices, Office Suite, SaaS, Windows, macOS|Access to systems where default credentials are still enabled or unchanged|


```
(P) Preparation

1. Use MFA.
2. Use network segmentation.
2. Disable or remove any unused default accounts.
3. Change all default passwords to align with organization's password guidelines/policies.
4. Audit and monitor usage for known default accounts.
 
```
  
Assign steps to individuals or teams to work concurrently, when possible; this playbook is not purely sequential. Use your best judgment.

--------------

### Investigate

### Key Questions

- **Was a default or vendor-supplied account used to access the system?**
- **Were the account credentials ever changed or disabled before deployment?**
- **What actions were performed with the exploited default account?**

1. Identify the account used.
2. Examine any processes started, files accessed, or changes made during account usage.
3. Determine if the account's credentials were changed, re-enabled, or left with default passwords.
4. Look for lateral movement.
5. Check for privilege escalation.
6. Focus on anomalies around login behavior, especially any vendor or legacy system accounts.

--------------

### Remediate

* **Plan remediation events** where these steps are launched together (or in coordinated fashion), with appropriate teams ready to respond to any disruption.
* **Consider the timing and tradeoffs** of remediation actions: your response has consequences.

#### Contain

1. **Isolate the affected host**
2. **Disable/lock the default account**
3. **Reset default account credentials**
   - Change passwords for the exploited default account across all systems.
   - Avoid future reuse.
4. **Restrict/revoke login permissions**
5. **Alert SOC Tier 2 or IR Team**

#### Eradicate

1. **Remove unused default accounts**
   - Document any changes made and confirm no automated systems are impacted.
2. **Review and adjust default account permissions to follow the principle of least privilege.**
3. **Scan for persistence mechanisms**

--------------

### Communicate

*Refer to organization's Incident Response Communication Plan for escalation matrix, timing, and format.*    

--------------

### Recover

In addition to the general steps and guidance in the incident response plan:

1. **Restore affected systems from clean backups.**
2. **Re-enable secured accounts.**
   - Default accounts should only be reinstated if absolutely necessary.
3. **Verify compliance with least privilege.**
4. **Test logging/alerting functions.**
   - Confirm that alerting is triggered for use of default accounts.
5. **Log all recovery activities.**
   - Prepare data for the post-incident review.

--------------
  
### Lessons Learned

1. Default accounts are common overlooked attack vectors.
2. Validate that all deployed systems are following secure baseline configurations.
3. Determine what password guidelines and policies need reinforcement.
4. Determine whether there are any detection gaps that need addressing.
5. Train teams to identify and disable/secure default accounts during provisioning.

--------------

### Resources

#### Additional Information

- Playbook template adapted from [Incident-Playbook by austinsonger](https://github.com/austinsonger/Incident-Playbook), licensed under the MIT License.


