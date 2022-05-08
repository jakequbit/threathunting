# threathunting
<h4>All things I use (or have used) for threat hunting!</h4>
<p>Hey! I'm glad you could make it. Below is just a hodge-podge of all the resources I use to Threat Hunt. I'll try to add anecdotes and use cases next to each piece, but at the very least EVERYTHING will have a link.

<h2>Frameworks</h2>
<p>The beginning of Threat Hunting is an intimate understanding of foundational frameworks and methodologies. (It's not as deep as it sounds)</p>

- [MITRE ATT&CK](https://attack.mitre.org)
    - To get started: [Getting Started with ATT&CK](https://medium.com/mitre-attack/getting-started/home)
- [MITRE D3FEND](https://d3fend.mitre.org) - If you've successfully mapped to ATT&CK IDs, your stakeholders will almost certainly ask: 'Now what?'
    - You'll find the answers here: [ATT&CK Mitigations to D3FEND Technique Mappings](https://d3fend.mitre.org/mappings/attack-mitigations)
    - Map by specific ATT&CK ID: [ATT&CK ID to D3FEND MAPPER](https://d3fend.mitre.org/tools/attack-mapper)
- [MITRE CAR](https://car.mitre.org/)
- [Cyber Kill Chain](https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html)

<h2>Tools for the Hunt</h2>
<h4>Enterprise</h4>
General Data Sources

- SIEM (Splunk, ArcSight, LogRhythm, Elastic)
- Firewalls, IDS/IPS (Palo Alto, Cisco, Fortinet)
- Endpoint Detection and Response (EDR) (Falcon, Carbon Black, MD4E)
- DNS Monitoring (it's always DNS) (SolarWinds (haaaa), Nagios, ManageEngine etc)
- pcap tap tap (Snort, WireShark, PRTG)


<h4>Testing Detection Capabilities</h4>

- [exploit-db](https://www.exploit-db.com/) - access to direct exploits for simulating advanced attacks in your enviornment
- [Atomic Red Team](https://github.com/redcanaryco/atomic-red-team) - I use Red Canary's Atomic Red Team to test detection and imho it's the best MVP (both minimal viable product and most valuable player). (bonus: it's mapped to MITRE!) 


No list would be complete without Sysmon...

<h4>Sysmon</h4>

- [Sysmon](https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon) - sysmon adds MUCH better logs to windows event log. You'll get entire commands for processes, file hash records (sha1,256 and md5), and see what drivers or DLLs are being loaded with signatures + more. Also, if you need a cheap way to implement better logging on windows (or linux) endpoints, this is a solid mitigation. 


<h4>IOC Analytics</h4>
<p>These are just some open source tools I use to help enrich or give context to any traditional IOC's I might be working with.</p>

- [DNSLytics](https://dnslytics.com/)
- [AbuseIPDB](https://www.abuseipdb.com/)

<h2>Use Cases</h2>

This section is mostly documenting my thoughts on use cases as I go... obviously these will be more free form based on my understanding of TTPs and less about known IOCs, though I do find these ideas sometimes follow patterns of indicators of attack (IOAs)

- Office products spawning cmd.exe or powershell.exe
- http user agents that are anomolous or old as dirt (aka riddled with vulns)
- internal to external connections on timed patterns on asynchronous ports
- executives and windows auth logs, baselining the norm to identify the anomolies
- Log4j, unfortunately this won't go away for a long time... check for outgoing LDAP or RMI traffic

<h2>Excellent Reads/Watches</h2>
<p>Got tools but need inspiration for a hunt?</p>

- [THREAT HUNTING: 10 ADVERSARY BEHAVIORS TO HUNT FOR](https://www.cybersecurity-insiders.com/threat-hunting-10-adversary-behaviors-to-hunt-for/)
- [Threat Hunting Playbook with Specific Use Cases](https://cdn2.hubspot.net/hubfs/2539398/Rank%20Software_Threat%20Hunting%20Playbook.pdf)
