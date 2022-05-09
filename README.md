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

<h2>Getting Started: The General Playbook</h2>
<p>Steps of Threat Hunting, trying to make the process as repeatable as process for the end goal of automation and dissemination with program metrics.</p>

1. <b>Coming up with a hypothesis:</b> this will be your 'why or what', what is the use case you're hunting for? See inspiration below.
2. <b>Identify, process and/or collect intelligence:</b> You'll want to determine which tools and information you need. Helpful: You might find that the business is not currently collecting data that would be useful to your investigation, this itself is a potential threat to the business and should be documented!
3. <b>Investigate:</b> Now that your data is collected and organized, start hunting! search for the criteria matching your hypothesis or use case and see what you find!
4. <b>Scenario: Triage (others sometimes refer to this as the 'trigger'):</b> If you found evidence of a potentially compromised asset, you'll want to triage this through the IR team (unless you are also the IR team, then you'll converge your information into Root Cause Analysis (RCA))
5. <b>Feedback / Automation:</b> Throughout the process of your hunt, were there any pieces you could automate? Any tools that you can schedule hunting tasks? Any way to improve your handoff? 

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
- [Amass](https://github.com/OWASP/Amass) - A great way to hunt for subdomains and map out your attack surface 

<h4>Data Sources / Monitoring Tools</h4>
<p>Once you have a hypothesis, or a start/inspiration for your hunt, you'll have to find where pertinent information is collected or identify new information that should be collected.</p>

- [Shodan.io](https://www.shodan.io) - Shodan can be a great way to start a Threat Hunt. It's way too common to discover X system may have been public for far too long.

In addition to the general tools used above: No list would be complete without Sysmon...

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

- [THREAT HUNTING: 10 ADVERSARY BEHAVIORS TO HUNT FOR](https://www.cybersecurity-insiders.com/threat-hunting-10-adversary-behaviors-to-hunt-for/) - good use cases for hypothesis
- [Threat Hunting Playbook with Specific Use Cases](https://cdn2.hubspot.net/hubfs/2539398/Rank%20Software_Threat%20Hunting%20Playbook.pdf) - good use cases for hypothesis
- [Yara Rules Guide](https://www.varonis.com/blog/yara-rules) - YARA rules are searches to find files that match specific criteria you're looking for, powerful when you have a good hypothesis
- [Google Hacking Database (GHDB)](https://www.exploit-db.com/google-hacking-database) - basically an encyclopedia of dorks searches to reveal vulnerable servers and web apps via common vulnerabilities 
- [Using Dorks to Find Vulnerable Services](https://www.youtube.com/watch?v=u_gOnwWEXiA) - a good video to get started with dorks, this could be a solid start to a find vulns to display on your HackerOne 
- [Threat Hunting Maturity Model](http://detect-respond.blogspot.com/2015/10/a-simple-hunting-maturity-model.html) - If you're starting or leading a threat hunting program this is an excellent resource to help you understand what the capability and goals of your team should be
- [Another Paper on the Maturity Model for Threat Hunting](https://www.threathunting.net/files/framework-for-threat-hunting-whitepaper.pdf)
- [Threat Hunter Playbook By Roberto Rodriguez @Cyb3rWard0g](https://threathunterplaybook.com/library/windows/active_directory_replication.html) - This is gold. A literal treasure and a huge inspiration to me for starting this repo.

<h2>Helpful Repos</h2>

- [Yara Rules](https://github.com/Yara-Rules/rules) - a full repo of different types of rules for different use cases
- [Awesome Threat Hunting](https://github.com/0x4D31/awesome-threat-detection) - PS There's a ton of awesome lists out there for more than just Threat Hunting
