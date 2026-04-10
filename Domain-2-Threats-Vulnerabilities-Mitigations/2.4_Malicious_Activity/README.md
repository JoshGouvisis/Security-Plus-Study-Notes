# 2.4 Indicators of Malicious Activity

Security professionals must recognize the technical signs (Indicators of Compromise) that an attack is occurring or has occurred.

## Malware Types
* **Ransomware:** Encrypts files and demands payment for the decryption key.
* **Trojan Horse:** Malicious software disguised as legitimate software.
* **Worm:** Self-replicating malware that spreads across a network without human intervention.
* **Rootkit:** Designed to hide its presence and maintain privileged (root) access to a system.
* **Spyware:** Secretly monitors user activity (keystrokes, browsing) and sends it to an attacker.

## Technical Indicators (IoCs)
* **Account Changes:** Unauthorized creation of new admin accounts or password resets.
* **Network Anomalies:** Spikes in outbound traffic to unknown geographic locations.
* **File Changes:** Unexpected changes to system binaries or the presence of unknown processes.

## ⚙️ Malware Execution & Persistence
* **Logic Bomb:** Malware that triggers when a specific event occurs (e.g., a date or a user being deleted).
* **Fileless Malware:** Operates only in the system's RAM (memory) to avoid detection by disk-based antivirus.
* **Command and Control (C2):** The external server that sends instructions to a botnet.
* **Backdoor:** A method of bypassing normal authentication to maintain access to a system.
* **Keylogger:** Software that records every keystroke to steal passwords and sensitive data.
