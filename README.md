# BeCode Corp. - Secure Network Design 🏢🔒

Welcome to the repository for the **BeCode Corp. Secure Network Design** project. 
This repository centralizes all configurations, simulations, and documentation required to build a secure, scalable, and efficient enterprise network from scratch.

## 🎯 Project Overview
The objective of this project is to design the network infrastructure for the new BeCode Corp. office. We are using **Cisco Packet Tracer** to simulate and validate the network's connectivity, performance, and security.

### 🛡️ Key Security & Network Features
* **Network Segregation:** Implementation of VLANs across five distinct company sectors (Management, Study, Production, Support, IT).
* **DMZ Implementation:** Secure isolation of external-facing services using VLANs and Access Control Lists (ACLs).
* **Core Services:** Configuration of DNS, DHCP, and an FTP storage server.
* **Access Management:** Centralized AAA (Authentication, Authorization, and Accounting) service implementation.
* **Traffic Filtering:** Strict ACL routing to secure communication between departments and critical servers.
graph TD
    %% Définitions de style (Texte forcé en noir avec color:#000000)
    classDef cloud fill:#e0f7fa,stroke:#006064,stroke-width:2px,color:#000000;
    classDef router fill:#ffcc80,stroke:#e65100,stroke-width:2px,color:#000000;
    classDef routerOff fill:#eeeeee,stroke:#9e9e9e,stroke-width:2px,stroke-dasharray: 5 5,color:#555555;
    classDef switchCore fill:#b39ddb,stroke:#4a148c,stroke-width:2px,color:#000000;
    classDef switchAcc fill:#c5cae9,stroke:#1a237e,stroke-width:2px,color:#000000;
    classDef vlan fill:#f1f8e9,stroke:#33691e,stroke-width:1px,color:#000000;

    %% Noeuds (Equipements)
    WAN((Internet / Cloud)):::cloud
    R1{R-CORE-01<br>Routeur Actif}:::router
    R2{R-CORE-02<br>Warm Spare}:::routerOff
    SW_CORE[SWITCH CORE<br>L3 - Distribution]:::switchCore
    SW_A[SW-A : DataCenter]:::switchAcc
    SW_B[SW-B : Bureaux]:::switchAcc
    SW_C[SW-C : Operations]:::switchAcc
    
    %% Noeuds (VLANs)
    V100[VLAN 100 : DMZ<br>DNS x2, DHCP, FTP, AAA]:::vlan
    V10[VLAN 10 : Management<br>5 PC + 1 Imprimante]:::vlan
    V20[VLAN 20 : Study<br>8 PC]:::vlan
    V30[VLAN 30 : Production<br>10 PC]:::vlan
    V40[VLAN 40 : Support A<br>10 PC]:::vlan
    V41[VLAN 41 : Support B<br>10 PC]:::vlan
    V50[VLAN 50 : IT Dept<br>5 PC]:::vlan

    %% Connexions physiques et logiques
    WAN --- R1
    WAN -.-x|Debranche| R2
    
    R1 ===|Trunk 802.1Q| SW_CORE
    
    SW_CORE ===|EtherChannel| SW_A
    SW_CORE ===|EtherChannel| SW_B
    SW_CORE ===|EtherChannel| SW_C
    
    SW_A --- V100
    SW_B --- V10
    SW_B --- V20
    SW_C --- V30
    SW_C --- V40
    SW_C --- V41
    SW_C --- V50
## 📂 Repository Structure
*(This section will be updated as we build the folder structure)*
