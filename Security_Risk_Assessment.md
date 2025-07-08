# **Security Risk Assessment: Social Media Data Breach**

## **Incident Summary**

A social media organization recently experienced a major data breach, leading to the compromise of customers' personal information (names and addresses). This breach was attributed to undetected vulnerabilities within the network. As a security analyst, I conducted an assessment to identify these vulnerabilities and propose effective network hardening practices to prevent future incidents.

## **1\. Identified Network Vulnerabilities**

Upon inspecting the organization's network, the following four major vulnerabilities were discovered:

1. **Shared Passwords Among Employees:** This practice significantly increases the risk of unauthorized access. If one employee's password is compromised, all accounts sharing that password are at risk. It also makes accountability difficult to trace.  
2. **Default Administrative Database Password:** The database's administrative account still used its default password. Default credentials are widely known and are a prime target for attackers, making them extremely vulnerable to brute force attacks or simple dictionary attacks.  
3. **Lack of Firewall Rules for Traffic Filtering:** The firewalls were not configured with specific rules to filter incoming and outgoing network traffic. This means the network is exposed to a wide range of external threats and allows potentially malicious internal traffic to leave the network undetected.  
4. **Absence of Multi-Factor Authentication (MFA):** MFA was not implemented for any accounts. This leaves accounts vulnerable to compromise even if passwords are stolen or guessed, as there is no secondary layer of verification.

If these vulnerabilities are not addressed, the organization faces a high risk of future data breaches, unauthorized access, and other cyberattacks.

## **2\. Selected Hardening Tools and Methods to Implement**

To address the identified vulnerabilities and enhance the organization's security posture, the following network hardening tools and methods are recommended:

1. **Multi-Factor Authentication (MFA)**  
2. **Firewall Maintenance (specifically implementing robust Port Filtering)**  
3. **Password Policies (focusing on strong, unique passwords and preventing default/shared usage)**

## **3\. Recommendations and Effectiveness**

### **Recommendation 1: Implement Multi-Factor Authentication (MFA)**

* **Vulnerability Addressed:** Directly addresses the "MFA is not used" vulnerability and significantly mitigates the risk associated with "employees sharing passwords" and "default admin password" by adding a crucial second layer of security.  
* **Why it is Effective:** MFA requires users to verify their identity using at least two different factors (e.g., something they know like a password, something they have like a phone/token, or something they are like a fingerprint). Even if an attacker manages to obtain a password through a brute force attack, phishing, or other means, they would still need access to the second factor, making unauthorized access exponentially more difficult. This drastically reduces the success rate of credential-based attacks.  
* **How Often to Implement:** MFA is primarily a one-time setup per account/system. However, it requires **consistent enforcement and maintenance**. This includes:  
  * **Initial Setup:** For all administrative and user accounts.  
  * **Ongoing Enforcement:** Ensuring MFA remains active for all critical systems.  
  * **User Training:** Regular training to educate employees on why MFA is important and how to use it securely.  
  * **Review:** Periodic review of MFA configurations and methods to ensure they remain robust against evolving threats.

### **Recommendation 2: Implement Robust Firewall Maintenance with Port Filtering**

* **Vulnerability Addressed:** Directly addresses the "firewalls do not have rules in place to filter traffic" vulnerability.  
* **Why it is Effective:** Firewall maintenance involves regularly checking and updating security configurations. A key aspect of this is **port filtering**, which allows or blocks specific port numbers to control network communication. By implementing strict port filtering rules, the organization can:  
  * **Reduce Attack Surface:** Close unused or unnecessary ports, preventing attackers from gaining entry points.  
  * **Control Traffic Flow:** Only allow legitimate traffic (e.g., web traffic on port 80/443, DNS on port 53\) while blocking all other unsolicited incoming connections.  
  * **Prevent Unauthorized Access:** Block known malicious ports and restrict outbound connections that could indicate malware activity or data exfiltration.  
  * **Mitigate DoS Attacks:** Basic rate limiting and connection tracking can be implemented at the firewall level to help defend against certain DoS attacks.  
* **How Often to Implement:** Firewall maintenance and port filtering should be an **ongoing and regular process**:  
  * **Initial Configuration:** Immediately implement a "deny all, permit by exception" rule set.  
  * **Regular Review:** At least monthly, review firewall logs and rules to identify suspicious patterns or outdated rules.  
  * **Event-Driven Updates:** Update rules immediately in response to new threat intelligence, discovered vulnerabilities, or changes in network services.

### **Recommendation 3: Enforce Strong Password Policies**

* **Vulnerability Addressed:** Directly addresses "employees share passwords" and "admin password for the database is set to the default."  
* **Why it is Effective:** Strong password policies are fundamental to preventing brute force attacks and credential compromise. Effective policies should focus on:  
  * **Complexity:** Requiring a minimum length, combination of character types (uppercase, lowercase, numbers, symbols), and avoiding common patterns or dictionary words.  
  * **Uniqueness:** Prohibiting the reuse of previous passwords and encouraging unique passwords across different services.  
  * **Prevention of Defaults:** Mandating immediate change of all default passwords upon system deployment.  
  * **No Sharing:** Strictly enforcing a policy against password sharing among employees, coupled with individual accountability.  
  * **Salting and Hashing:** Ensuring passwords are stored securely using modern cryptographic hashing techniques (though this is more of a system implementation than a policy users directly interact with).  
* **How Often to Implement:** Password policies are **established once but require continuous enforcement and monitoring**:  
  * **Initial Implementation:** Define and communicate the policy to all employees.  
  * **System Enforcement:** Configure systems (e.g., Active Directory, web application login forms) to enforce the policy rules.  
  * **Employee Training:** Regular security awareness training to educate employees on the importance of strong, unique passwords and the risks of sharing.  
  * **Monitoring Login Attempts:** Implement systems to monitor and alert on excessive failed login attempts (e.g., account lockout policies).  
  * **Periodic Review:** Review the effectiveness of the policy and update it as new attack techniques emerge.

These combined measures create a robust defense-in-depth strategy, significantly reducing the organization's attack surface and making it much harder for malicious actors to gain unauthorized access.