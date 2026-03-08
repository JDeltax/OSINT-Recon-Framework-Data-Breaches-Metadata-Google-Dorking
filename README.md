# OSINT and Digital Reconnaissance: Technical Infrastructure Audit

## Executive Summary
This project documents a technical workflow for Open Source Intelligence (OSINT) and digital forensics. The research focuses on the identification of organizational vulnerabilities through data breach correlation, host enumeration, and forensic metadata extraction. 

## Objectives
* Identification of compromised credentials and historical data leaks associated with specific domains.
* Execution of host and subdomain discovery to map the digital attack surface.
* Forensic analysis of file metadata to identify technical and geographical artifacts.
* Application of advanced search engine operators (Google Dorking) for the detection of exposed sensitive information.

## 1. Data Breach Investigation
The initial phase involved the correlation of domain assets with known data leak repositories.
* **Information Sources:** Research was conducted across specialized platforms including HaveIBeenPwned, F-Secure, HackNotice, BreachDirectory, and KeeperSecurity.
* **Findings:** Two distinct data breaches were confirmed, indicating historical exposure of credentials related to the target domain.

## 2. Infrastructure Enumeration and Harvesting
A comparative analysis was performed between legacy and modern reconnaissance tools.
* **Tool Migration:** The utility `emailharvester` was identified as obsolete for modern web environments. Consequently, the workflow transitioned to **theHarvester**.
* **Host Discovery:** Utilizing the `crtsh` and `rapiddns` modules, 52 unique hosts were successfully identified.
* **Scraping Limitations:** Analysis of exhaustive search results demonstrated that direct email scraping is frequently mitigated by contemporary security headers and Web Application Firewalls (WAF), necessitating the use of specialized APIs for further extraction.

## 3. Automated Intelligence Framework (Spiderfoot)
To enhance the depth of the reconnaissance, the Spiderfoot GUI was deployed to orchestrate multiple intelligence modules.
* **Modules Analyzed:** Ahmia, Dehashed, AccountFinder, Leak-Lookup, and EmailCrawlr.
* **Dark Web Assessment:** The Ahmia module was executed to verify the domain's presence within indexed .onion services. Results indicated zero public exposure on the Tor network, suggesting no immediate threats from prominent dark web marketplaces.

## 4. Metadata Forensics (Exiftool)
Metadata analysis was conducted to identify hidden information within digital assets that could compromise operational security.
* **Procedure:** Using `exiftool`, the technical attributes of a standard JPEG asset were parsed, revealing camera specifications, timestamps, and software versions.
* **Structured Reporting:** For large-scale audits, the following command was utilized to generate machine-readable reports:
  `exiftool -csv [filename] > metadata_report.csv`

## 5. Google Dorking and GHDB Integration
Advanced search operators were employed to isolate sensitive information indexed by search engines.
* **Core Operators:** `site:`, `filetype:`, `intitle:`, `inurl:`, and `allintext:`.
* **Methodology:** Queries were aligned with the Google Hacking Database (GHDB) standards to identify misconfigured servers, exposed log files, and administrative panels.

## 6. Evidence Documentation
The following captures provide empirical evidence of the procedures described above:
* **Figure 1:** Host identification via theHarvester.
* **Figure 2:** Analysis of scraping limitations in broad searches.
* **Figure 3:** Configuration of automated modules in Spiderfoot.
* **Figure 4:** Final assessment of Dark Web exposure.
* **Figure 5:** Detailed metadata extraction from forensic assets.
* **Figure 6:** CSV output for structured forensic analysis.

## Disclaimer
The information contained in this repository is for educational and ethical security auditing purposes only. The author is not responsible for the misuse of these techniques.
