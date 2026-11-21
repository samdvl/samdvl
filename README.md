# Simone Svanetti

**IT Systems Manager · Industrial Software Architect (OT/IT, ISA-95) · Applied AI & MLOps**

Over 9 years of hands-on experience bridging mission-critical IT infrastructures, industrial Level 2 software (ISA-95), and production Computer Vision systems.

> **Note on proprietary work:** Most of my production software and industrial integrations are developed under NDA for manufacturing, logistics, and regulated environments. This GitHub profile showcases anonymized architectural patterns alongside public AI/MLOps, software engineering, and embedded IoT repositories.

---

### Core Focus Areas

- **IT Infrastructure & Cybersecurity:** Autonomous design and management of multi-site infrastructures, VMware vSphere HA clusters, redundant industrial networking (MikroTik), Acronis disaster recovery, SIEM, and ISO/IEC 27001 & NIS2 operational alignment.
- **OT/IT Integration & Level 2 Software (ISA-95):** End-to-end C# / .NET development of resilient Windows Services, WPF operator HMIs, Siemens PLC integration (TIA Portal S7-1200, OPC UA, Sharp7, Snap7), AGV fleet orchestration (REST/JSON), MES/L3 interfacing, and industrial metrology software.
- **Applied Computer Vision & MLOps:** Training supervised models on Google Cloud Vertex AI and deploying them in production as offline or centralized HTTP REST inference services inside Docker containers, integrated directly with PLCs, relational databases, and MES validation workflows.

---

### Reference Architecture · Factory-to-AI (NDA-Safe Pattern)

High-level pattern representing the separation of concerns between shop-floor automation (L1), resilient C#/.NET orchestration and containerized ML inference (L2), and enterprise systems (L3):

```mermaid
flowchart LR
    subgraph L1["Level 1 · Shop Floor / OT"]
        PLC["Siemens PLC<br/>(OPC UA / Sharp7 / Snap7)"]
        CAM["Industrial Cameras &<br/>Mobile Touch Clients"]
    end

    subgraph L2["Level 2 · Orchestration & Edge AI"]
        SVC["C# / .NET Services<br/>(Resilient Workers & WPF HMI)"]
        AI["Docker Inference Service<br/>(TensorFlow / CV Models)"]
    end

    subgraph L3["Level 3 · Enterprise & Data"]
        DB["Relational DB<br/>(Oracle / MySQL / SQL Server)"]
        MES["MES / ERP &<br/>AGV Fleet (REST)"]
    end

    PLC <-->|"OT Protocols"| SVC
    CAM -->|"HTTP REST / USB"| SVC
    SVC <-->|"HTTP REST"| AI
    SVC <-->|"Stored Procs / Tables"| DB
    SVC <-->|"REST / Exchange Tables"| MES
