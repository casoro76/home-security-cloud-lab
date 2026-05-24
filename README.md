# Secure Home Network & Cloud Sandbox Integration

This repository contains the documentation, network topology, and configuration strategies for an isolated, zero-trust home lab environment integrated with a secure cloud testing sandbox. The objective of this project is to safely simulate threat environments, analyze network traffic, and practice advanced risk mitigation without risking exposure to production environments.

## Architecture & Design

### 1. Network Segmentation (Local Environment)
The local virtualized network is engineered using a strict segmentation model to enforce zero-trust principles:
* **Management Zone:** Isolated VLAN dedicated to administrative tasks, log aggregation, and infrastructure monitoring.
* **Attack Simulation Zone:** A contained subnet hosting penetration testing distributions (e.g., Kali Linux) to launch controlled exploits.
* **Target/Victim Zone:** An isolated subnet containing intentionally vulnerable virtual machines and legacy operating systems used to analyze exploit behavior.

Hardened firewall rules restrict all inter-VLAN traffic by default, enforcing the principle of least privilege. Ingress and egress traffic are strictly monitored, and any unauthorized lateral movement attempts are logged and dropped.

### 2. Cloud Sandbox Integration (AWS)
To practice cloud security best practices, the local environment securely connects to an isolated AWS cloud instance:
* **Virtual Private Cloud (VPC):** Deployed a custom VPC with dedicated public and private subnets.
* **Security Groups & Network ACLs:** Established restrictive, stateful firewall rules that block all inbound traffic by default, permitting only specific, encrypted administrative connections from authorized local IP addresses.
* **IAM Hardening:** Enforced Multi-Factor Authentication (MFA) and strict Identity and Access Management (IAM) policies, ensuring no root-account usage for daily operations.

## Capabilities & Use Cases
* **Traffic & Log Analysis:** Monitoring network traffic patterns to detect anomalies and baseline normal network behavior.
* **Vulnerability Testing:** Conducting safe, hands-on vulnerability assessments against target machines to understand exploitation vectors.
* **Incident Response Practice:** Simulating common attack scenarios to develop and refine structured incident response protocols and risk mitigation strategies.
