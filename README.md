[1.0] DESCRIPTION
-------------------------------------------------------------------------------
This project establishes a mission-critical, high-security bridge between 
Oracle EBS R12 and external banking SFTP portals[cite: 2]. The framework 
automates payment processing (IBFT, Salaries, Cheques) to eliminate manual 
entry risks while isolating the Production ERP from the public internet[cite: 2].


[2.0] ARCHITECTURAL DESIGN (Multi-Tier Security)
-------------------------------------------------------------------------------
To prevent direct WAN exposure of the core ERP, the following layers were 
implemented[cite: 2]:

  LAYER 1: EBS PRODUCTION ZONE (Internal)
           - Oracle Linux 6 environment.
           - Generates payment files and pushes to Gateway via LAN.

  LAYER 2: SECURITY GATEWAY / DMZ (Intermediate)
           - Hardened Oracle Linux 8 server.
           - Acts as the only node authorized to communicate with WAN.

  LAYER 3: BANK SFTP PORTAL (External)
           - Receives encrypted data via SSH V2 Public-Private Key trust.


[3.0] AUTOMATION STACK
-------------------------------------------------------------------------------
*   RSYNC: Scheduled 5-minute replication for data consistency[cite: 2].
*   INOTIFYWAIT: Real-time 24/7 directory monitoring for instant triggers[cite: 2].
*   EXPECT: Automated SSH handshaking (avoids hardcoded passwords)[cite: 2].
*   DATA GUARD: Full configuration sync for Disaster Recovery (DR).


[4.0] BUSINESS IMPACT
-------------------------------------------------------------------------------
*   EFFICIENCY: Zero manual intervention for batch payment processing.
*   SECURITY: One-way traffic logic (Gateway -> Bank) prevents ingress.
*   ACCURACY: Automated validation reduces human error in financial data.
*   PAPERLESS: Significant milestone in the corporate paperless initiative.


[5.0] REPOSITORY STRUCTURE
-------------------------------------------------------------------------------
/scripts
  |-- sync_prod_to_gateway.sh   (Automated rsync logic)
  |-- gateway_watcher.sh        (inotifywait trigger script)
  |-- bank_upload.exp           (Secure expect-based SFTP upload)
/docs
  |-- architecture_diagram.png  (Sanitized network layout)
  |-- security_sop.pdf          (Standard Operating Procedures)


[6.0] DATA PRIVACY COMPLIANCE
-------------------------------------------------------------------------------
CRITICAL: This repository has been fully sanitized. All IP addresses, 
hostnames, and organization-specific names have been replaced with 
placeholders (e.g., X.X.X.X) to protect corporate confidentiality.

[7.0] ARCHITECTURE 
--------------------------------------------------------------------------------
<img width="1408" height="768" alt="oracle-ebs-secure-bank-automation" src="https://github.com/user-attachments/assets/88ab0451-3539-4a01-8e79-dfeb9cc8ac4d" />

