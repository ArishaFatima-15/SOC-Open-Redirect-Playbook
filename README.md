**SOC Detection & Response Playbook - Open Redirect (Video Production Scenario)
**
## Objective:
Build a defensive monitoring and response playbook for detecting Open Redirect-style attack activity, framed as a SOC analyst protecting a Video Production organization. This project covers detection rules, alert-triage workflows, and an incident-response playbook.

## Research and Threat Overview:
* **Open Redirect Vulnerability:** Occurs when an application takes a parameter and redirects a user to an external URL without validation, often used in phishing campaigns targeting organizations.
* **Attack Indicator in Logs:** Presence of external domains (e.g., `http://evil-phishing-site.com`, `https://malicious.com`) passed through redirect query parameters (e.g., `?to=`, `?next=`, `?url=`).
* **Benign Traffic / False Alarm:** Normal internal path navigation or relative paths (e.g., `?to=/dashboard`, `?to=/#/about`).
## Deliverables:
* **Main Report:** You can view the complete detailed report document here: [SOC Detection and Response Playbook Report](./SOC_Detection_and_Response_Playbook_Open_Redirect_Report.pdf)
* **Detection Rule:** Splunk SPL query for catching external redirect payloads: 
  `source="juice_shop_access.log" "Unrecognized target URL for redirect" | regex _raw="(?i)redirect:\s*https?://(?!(github.com))" | table _time, host, _raw`
* **Test Logs:** Attack and benign log samples ([View Log File](./juice_shop_access.log)).
