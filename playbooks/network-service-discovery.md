## Playbook: Network Service Discovery
  
### MITRE

| Tactic | Technique ID | Technique Name | Platforms  | Permissions Required |
| ------ | ------------ | -------------- | ---------- |--------------------- |
|Discovery|T1046        |Network Service Discovery |Containers, IaaS, Linux, Network Devices, Windows, macOS|Access to an internal network segment or host with network visibility|


```
(P) Preparation

1. Enforce network segmentation.
2. Implement strict firewall rules.
3. Disable unused services and ports.
4. Limit administrative privileges.
5. Deploy endpoint and network detection tools.
6. Apply network access control.
7. Log and monitor internal traffic.
8. Conduct regular security awareness training.
 
```
  
Assign steps to individuals or teams to work concurrently, when possible; this playbook is not purely sequential. Use your best judgment.

--------------

### Investigate

#### Key Questions
- **What system/account initiated the network scanning activity?**
- **What targets were scanned, and which ports/protocols were involved?**
- **Was the scanning likely to be malicious activity or legitimate network operations?**

1. Review logs to find the host initiating the discovery.
2. Check for widespread port scans or focused probing of sensitive systems.
3. Look for signs of lateral movement.
4. Review command history, any PowerShell logs, or EDR data for signs that scanning tools were used.
5. Assess for additional malicious activity.

--------------

### Remediate

* **Plan remediation events** where these steps are launched together (or in coordinated fashion), with appropriate teams ready to respond to any disruption.
* **Consider the timing and tradeoffs** of remediation actions: your response has consequences.

#### Contain

1. **Isolate the affected endpoint**
   - Disconnect the system from the network.
2. **Block scanning traffic**
   - Limit port/protocol access where needed.
3. **Revoke credentials used in the scan**
   - Disable any accounts associated with the scanning activity.
   - Monitor for any reuse of revoked credentials.
4. **Restrict tools used for enumeration**
   - Remove any unauthorized tools/scripts from the endpoint.
5. **Alert and escalate to IR team**

#### Eradicate

1. **Remove any unauthorized discovery tools/scripts**
   - Identify and uninstall any port scanners or enumeration tools.
   - Delete any scripts or binaries used during discovery.
2. **Eliminate any persistence mechanisms used for repeated scanning**
3. **Reimage/clean any compromised systems (if required)**
   - Ensure no residual artifacts are left behind.
4. **Reconfigure misused services or open ports**
5. **Update detection/prevention rules**

--------------

### Communicate

*Refer to organization's Incident Response Communication Plan for escalation matrix, timing, and format.*    

--------------

### Recover

In addition to the general steps and guidance in the incident response plan:

1. Restore affected systems to operational state.
2. Re-enable any temporarily disabled services with proper hardening.
3. Update normal traffic baselines post-incident for improved anomaly detection.
4. Perform vulnerability/configuration scans.
5. Document recovery actions taken.
   - Update response documentation for future reference.

--------------
  
### Lessons Learned

 1. Review and refine detection rules for any abnormal internal scanning.
 2. Assess gaps in current network segmentation.
 3. Update necessary playbooks and IR procedures with new relevant information.
 4. Conduct a team debrief.
 5. Perform tabletop exercises focused on discovery attacks.

--------------

### Resources

#### Additional Information

- Playbook template adapted from [Incident-Playbook by austinsonger](https://github.com/austinsonger/Incident-Playbook), licensed under the MIT License.



