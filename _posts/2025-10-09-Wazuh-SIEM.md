---
layout: post
title: Wazuh - SIEM
longtitle: Wazuh - Open Source XDR. Open Source SIEM.
tags:
- SIEM
- Wazuh
date: 2025-10-09
---

**Wazuh** is a powerful, free, and open-source security platform that unifies **Security Information and Event Management** (SIEM) and **Extended Detection and Response** (XDR) capabilities into a single solution. It's designed to provide comprehensive security monitoring across diverse IT environments, including cloud workloads, virtualized systems, and on-premises endpoints.

The platform operates through a lightweight, cross-platform agent that collects, aggregates, and analyzes security data in real-time. Key components of its defense strategy include **File Integrity Monitorin**g (FIM), **log data analysis**, **intrusion detection**, **vulnerability detection**, and **security configuration assessment**.

## Core Security Mechanisms

A critical aspect of Wazuh's capabilities, particularly in **File Integrity Monitoring** (FIM), is its foundational reliance on **hashing**. Hashing uses widely available algorithms like SHA-256 and MD5 to generate a unique fixed-size string (a hash) for a file. By comparing the current hash of a file against a previously recorded baseline, Wazuh can instantly detect even the slightest unauthorized change to critical files, which is a key indicator of compromise.

## Advanced Threat Detection and Telemetry

Wazuh integrates with specialized tools for high-fidelity threat detection. For advanced malware detection, the Wazuh FIM module can be configured to integrate with **[YARA]({% link _posts/2025-10-09-YARA-Pattern-Matching-Swiss-Army-Knife.md %})**—a widely-used, open-source tool that helps security researchers identify and classify malware based on textual or binary patterns. When FIM detects a suspicious file creation or modification, it can automatically trigger a **YARA** scan, enhancing the system's ability to identify new and evolving threats.

Furthermore, Wazuh leverages granular telemetry from advanced endpoint security utilities, such as **Sysinternals Sysmon**, particularly for deeper host visibility and comprehensive File Integrity Monitoring on Windows systems. Sysmon's ability to monitor process creations, network connections, and detailed file activities generates rich event data. This data is collected by the Wazuh agent, which then forwards it to the Wazuh manager for decoding, analysis, and correlation with threat intelligence, providing analysts with the enriched context needed for effective threat hunting and incident response.

Through this combination of core features, foundational hash-based integrity checking, and extensible integrations, Wazuh provides a scalable, cost-effective, and highly customizable foundation for an organization's **Security Operations Center** (SOC)

## Installation

For our activity, we will utilize **[Docker]({% link _posts/2025-10-09-Deployment-Testing-and-Rapid-Deploy.md %})** to give a slight boost in setup and additional tool in our arsenal of deployment mechanisms.

### Git (source based) Install

> ##### Tip
>
> Make sure you have **Git**, and **Docker** installed.
>
{: .block-tip}

```shell
git clone https://github.com/wazuh/wazuh-docker --branch v4.13.1
```

### Use-Case & Running Wazuh

As the use-case for this activity is to have a local Wazuh to integrate **YARA** and **Sysmon**, we will only utilize the `single-node` setup.


```shell
cd wazuh-docker
cd single-node
docker compose -f generate-indexer-certs.yml run --rm generator
docker compose up -d
```

> ##### Tip
> 
> Carefully read the Terminal output as it will tell you how to access the containerized Wazuh SIEM that is now running on your workstation.
>
{: .block-tip}
