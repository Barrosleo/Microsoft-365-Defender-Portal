# Microsoft 365 Defender Portal

Microsoft 365 Defender Portal is the central security hub for organizations using Microsoft 365. It detects, investigates, and responds to security incidents affecting identities, endpoints, email, and collaboration tools.

If your organization uses only Microsoft 365, this portal offers:
- **Incident Management:** A unified view of security events for rapid investigation.
- **Threat Hunting:** Advanced query tools (using Kusto Query Language - KQL) to proactively search for potential attacks.
- **Security Posture Monitoring:** Actionable recommendations via Secure Score and threat analytics.

## Key Components of Microsoft 365 Defender

---

1. **Incident & Alert Management**
   - Collects and correlates security alerts from Microsoft 365 services (e.g., Exchange Online, Defender for Endpoint).
   - Alerts are grouped into incidents that include Severity, Category (e.g., phishing, malware), and Impacted Assets (user accounts, devices, mailboxes).

---

2. **Action Center**
   - Serves as a tracking dashboard for alerts and incident activities.
   - Allows security analysts to filter, manage, and resolve incidents systematically.

---

3. **Secure Score**
   - Audits security posture across identities, Microsoft apps (Exchange, Teams), and devices.
   - Provides actionable recommendations to address vulnerabilities.

---

4. **Threat Analytics Dashboard**
   - Displays global threat intelligence including common attack techniques (e.g., ransomware, phishing) and their impact on the environment.
   - Enables proactive analysis of high-risk vulnerabilities and alerts.

---

5. **Attack Simulation Training**
   - Enables simulation of incidents for hands-on training.
   - Helps develop incident response skills by investigating real-world threat patterns.

---

6. **Advanced Threat Hunting with KQL**
   - Uses Kusto Query Language (KQL) to search logs for hidden threats.
   - Analysts can use built-in or custom queries; for example:

   ```kusto
   SigninLogs
   | where ResultType != 0
   | extend Country = tostring(LocationDetails.CountryOrRegion)
   | summarize FailedAttempts = count() by IPAddress, Country, bin(TimeGenerated, 1h)
   | where FailedAttempts > 5
   ```
   This query detects multiple failed sign-ins from different locations, potentially indicating brute-force attacks.
   
---

## Summary

- **Centralized Management:** Monitor, investigate, and respond to security incidents through a unified portal.

- **Proactive Threat Hunting:** Utilize KQL and advanced dashboards to hunt and analyze emerging threats.

- **Security Posture Improvement:** Leverage Secure Score to continuously strengthen your Microsoft 365 security posture.

- **Training & Simulation:** Use attack simulation training to prepare your team for real-world threats.

---

## Getting Started

***Prerequisites:***

- Microsoft 365 Defender subscription/license

- Relevant Azure AD security permissions (e.g., Security Reader, Security Administrator)

- Git and a modern web browser

- Python 3.9+ (for automation scripts and notebooks)

---

## Installation:

***1. Clone the repository:***

```bash
git clone https://github.com/YourGitHubUsername/Microsoft-365-Defender-Portal.git
cd Microsoft-365-Defender-Portal
```

***2. Optional:*** Set Up a Python Virtual Environment:

```bash
python -m venv venv
source venv/bin/activate   # On Windows: .\venv\Scripts\activate
pip install -r requirements.txt
```

***3. Review the Documentation:*** Check out the files under the docs/ folder for detailed information on configuration, incident management, threat analytics, and more.

---

## Usage Examples

***Example Workflow: Investigate a Security Incident***

  1. **Analyze Alerts with KQL:** Use the sample query in `queries/failed_signins.kql` to `detect brute-force attempts.

  2. **Review Incident Details:** Read the documentation in `docs/Incident_Management.md` for incident grouping, severity, and response steps.

  3. **Track and Resolve Incidents:** Explore the Action Center functionality as described in `docs/Action_Center.md`.

  4. **Monitor Security Posture:** Review Secure Score insights from `docs/Secure_Score.md` and the corresponding dashboard in `dashboards/Secure_Score_Insights.json`.

  5. **Simulate Attacks and Train Your Team:** Run the attack simulation training script in `automation/simulation_training.py` and check the guidelines in`docs/Attack_Simulation_Training.md`.

  6. **Hunt for Threats:** Open the notebook `notebooks/Defender_Hunting_Tutorial.ipynb` for a deep dive into threat hunting using KQL.

---

## Supporting Resources & Documentation

- Incident Management

- Action Center

- Secure Score

- Threat Analytics

- Attack Simulation Training

- Advanced Threat Hunting

- Defender API Integration (if applicable)

---

## Technical Considerations

- **Programming Languages:** Python, KQL, Markdown, JSON, HTML/CSS/JavaScript (for dashboards)

- **Tools & Frameworks:** Microsoft 365 Defender, Azure AD, Flask (for dashboards), Jupyter Notebooks for tutorials

- **Deployment:** Local machine, cloud environments (via Azure), or integration with Microsoft 365 Defender’s portal

- **Version Control:** Git; follow best practices for commit messages and branching

---

## Desired Outcomes / Impact

- Enhance SOC efficiency by centralizing incident management and threat hunting.

- Improve security posture using actionable insights from Secure Score and threat analytics.

- Provide effective training through simulated attack scenarios.

- Empower security analysts with advanced KQL-based threat hunting capabilities.

---

## Contributing

We welcome contributions! Please see our `CONTRIBUTING.md` for details on how to report issues, suggest features, and submit pull requests.

---

## License

This project is licensed under the MIT License – see the `LICENSE` file for details.

---

## Acknowledgements

- **Microsoft 365 Defender Team:** For their ongoing innovation in cloud security.

- **Security Communities:** Inspiration drawn from the broader cybersecurity community and industry-standard frameworks like MITRE ATT&CK.

- **Attack Simulation & Threat Hunting Contributors:** Thanks to researchers and analysts who share their knowledge through GitHub.
