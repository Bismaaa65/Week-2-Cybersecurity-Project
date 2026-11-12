# Week 2 Cybersecurity Practical Project

## Overview

This repository documents two completed Week 2 cybersecurity practical
modules:

1.  **W2-PM4 -- Footprinting and Reconnaissance using theHarvester**
2.  **W2-PM5 -- Network Scanning using Zenmap (Nmap)**

The work covers passive information gathering for the domain specified
in the lab and host discovery on the user's own local Wi-Fi network.

> **Scope and authorization:** The PM4 exercise used `microsoft.com` as
> specified in the supplied lab instructions. PM5 was limited to the
> local network `192.168.100.0/24`. Network scanning should only be
> performed on systems and networks for which permission has been
> granted.

## Tools and Environment

  Tool / Environment                   Purpose
  ------------------------------------ ------------------------------------------------
  Kali Linux                           Environment for theHarvester practical
  theHarvester 4.11.1                  Domain footprinting and reconnaissance
  Baidu                                PM4 Task 1 search source
  All available theHarvester sources   PM4 Task 2 search selection
  Windows                              Environment for the network-scanning practical
  Zenmap / Nmap 7.993                  Local network host discovery
  VMware Workstation                   Kali Linux virtual machine

------------------------------------------------------------------------

## PM4 -- Footprinting and Reconnaissance with theHarvester

**Target domain:** `microsoft.com`

### Task 1 -- Search using Baidu

**Command:**

``` bash
theHarvester -d microsoft.com -l 1000 -b baidu
```

**Parameters:**

-   `-d`: target domain
-   `-l`: maximum result limit
-   `-b`: data source

**Observed results from the saved output:**

  Result type         Count
  ----------------- -------
  IP addresses            0
  Email addresses         0
  People                  0
  Hosts                   0

The Baidu search completed without returning IP addresses, email
addresses, people, or hosts in this run.

### Task 2 -- Search using all available sources

**Command:**

``` bash
theHarvester -d microsoft.com -l 50 -b all
```

**Summary reported by the saved output:**

  Result type          Count
  ------------------ -------
  ASNs                    10
  Interesting URLs        10
  LinkedIn users           0
  LinkedIn links           0
  IP addresses           161
  Email addresses          3
  People                   0
  Hosts                9,959

Additional source-specific messages in the output:

-   Hudson Rock reported 44 hosts, 0 IPs, and 0 emails.
-   Windvane reported finding 14 subdomains using DNS fallback.
-   Several providers could not be queried because their API keys were
    missing.
-   Fofa reported invalid credentials, and LeakIX reported an incorrect
    API key.

**Important interpretation:** These are counts reported by theHarvester
during this particular run. They are not independently verified, and
results can vary by source availability, configuration, and time. The
missing API keys mean some sources did not provide results.

### PM4 Evidence

Place the corresponding screenshots in a folder named `screenshots/` and
use these filenames:

-   `pm4-task1-baidu.png` -- Task 1 command and output
-   `pm4-command-history.png` -- commands used for both PM4 tasks
-   `pm4-task2-all-sources.png` -- Task 2 output and source/API-key
    messages

The raw output files were saved in Kali Linux at:

``` text
~/Week2_Project/PM4_theHarvester/Task1_Baidu/Task1_Baidu_Output.txt
~/Week2_Project/PM4_theHarvester/Task2_AllSources/Task2_AllSources_Output.txt
```

------------------------------------------------------------------------

## PM5 -- Network Scanning with Zenmap

### Network configuration

The Wi-Fi adapter details recorded during the practical were:

  Setting                    Value
  -------------------------- ---------------------
  IPv4 address               `192.168.100.23`
  Subnet mask                `255.255.255.0`
  Default gateway            `192.168.100.1`
  Local subnet scanned       `192.168.100.0/24`
  Laptop Wi-Fi MAC address   `34-F3-9A-6A-6E-04`

### Scan configuration

-   **Target:** `192.168.100.0/24`
-   **Profile:** Ping scan
-   **Nmap command shown by Zenmap:**

``` bash
nmap -sn 192.168.100.0/24
```

### Observed scan results

The Zenmap output reported 256 IP addresses scanned and 2 hosts up.

  -----------------------------------------------------------------------
  Live host                           Observation
  ----------------------------------- -----------------------------------
  `192.168.100.1`                     Router; MAC shown as
                                      `F0:2F:A7:44:C0:68` (Huawei
                                      Technologies)

  `192.168.100.23`                    Local laptop
  -----------------------------------------------------------------------

**Scan duration:** approximately 13 seconds in the submitted screenshot.
The earlier saved scan output recorded approximately 15.23 seconds; scan
duration can vary between runs.

### PM5 Evidence

Place the corresponding screenshots in `screenshots/` and use these
filenames:

-   `pm5-ipconfig.png` -- Wi-Fi IPv4 address, subnet mask, and gateway
-   `pm5-mac-address.png` -- Wi-Fi adapter physical address
-   `pm5-zenmap-scan.png` -- Zenmap Nmap Output showing the two live
    hosts
-   `pm5-topology.png` -- Zenmap topology view
-   `pm5-topology.pdf` -- exported topology PDF, if included as a
    separate file

------------------------------------------------------------------------

## Key Learning Outcomes

-   Practiced passive footprinting and reconnaissance with theHarvester.
-   Compared results from a single search source with results from the
    all-sources option.
-   Interpreted result counts and recognized API-key and
    provider-availability limitations.
-   Used Zenmap to perform a Ping Scan on a local network.
-   Identified active hosts and reviewed basic network configuration
    details.
-   Documented commands, findings, and screenshots for a practical
    cybersecurity report.

## Conclusion

The two practical modules provided experience with domain reconnaissance
and local network host discovery. PM4 demonstrated how theHarvester
gathers information from different sources and how source/API
limitations affect the results. PM5 demonstrated how Zenmap can identify
active hosts on a local subnet and present scan findings and topology
information.

## Repository Structure

``` text
Week-2-Cybersecurity-Project/
├── README.md
├── screenshots/
│   ├── pm4-task1-baidu.png
│   ├── pm4-command-history.png
│   ├── pm4-task2-all-sources.png
│   ├── pm5-ipconfig.png
│   ├── pm5-mac-address.png
│   ├── pm5-zenmap-scan.png
│   └── pm5-topology.png
└── reports/
    └── pm5-topology.pdf
```

*Add only the evidence files that are actually included in the
repository. Update screenshot filenames in this README if different
names are used.*
