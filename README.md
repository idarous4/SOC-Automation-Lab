## SOC Automation Lab – Unauthorized Login Response Playbook

This project demonstrates how to automate an incident response workflow using Splunk, Shuffle SOAR, Slack, and Active Directory. It focuses on detecting unauthorized logins, notifying a SOC analyst, and optionally disabling compromised user accounts.

## **Objective**

Automate detection and response to unauthorized logins by triggering an analyst-reviewed decision process that can disable a compromised Active Directory account via SOAR tools.

## **Skills Learned**

- Building automated workflows with Shuffle SOAR  
- Triggering playbooks from Splunk alerts  
- Integrating Slack for SOC notifications  
- Interacting with Active Directory to disable user accounts  
- Incorporating human-in-the-loop decisions into automation  
- Designing and documenting security orchestration flow

## **Tools Used**

- Splunk (alert detection and SIEM)  
- Shuffle SOAR (automation platform)  
- Slack (SOC notification and analyst action)  
- Active Directory (domain account control)  
- Windows Server (Domain Controller, Test Machine)  
- Virtual Infrastructure (e.g., Vultr)

## **Architecture Overview**

[<img src="./Architecture%20Overview.png" width="1000"/>](./Architecture%20Overview.png)

---

## **Workflow Summary**

1. **Detection:**
   - An attacker successfully authenticates to a test machine (Windows domain-joined).
   - Splunk ingests telemetry from the domain controller and test machine.

2. **Trigger Automation:**
   - Splunk alert is generated from unauthorized login activity.
   - Alert triggers a playbook in Shuffle SOAR.

3. **SOC Notification:**
   - Shuffle sends alert details to Slack.
   - SOC analyst receives a message asking whether to disable the affected user account.

4. **Decision Flow:**
   - If the analyst approves, Shuffle disables the domain account via Active Directory.
   - If denied, the playbook exits with no action taken.

5. **Logging & Reporting:**
   - Actions are logged in Splunk and documented for incident review.
