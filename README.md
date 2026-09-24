# SNORT

Study notes on **Snort**, the open-source, rule-based Network Intrusion Detection and Prevention System (NIDS/NIPS). Snort was created by Martin Roesch and is maintained by open-source contributors and the Cisco Talos team.

> "Snort is the foremost Open Source Intrusion Prevention System (IPS) in the world. Snort IPS uses a series of rules that help define malicious network activity and uses those rules to find packets that match against them and generate alerts for users."

## Contents

| Note | Topic |
|------|-------|
| [Main](Main.md) | Overview and key concepts |
| [Setup](Setup.md) | Installing and configuring Snort |
| [Mode 1: Sniffer](Operation%20mode%201%20SNIFFER.md) | Reading and displaying packets live |
| [Mode 2: Logger](Operation%20mode%202%20LOGGER.md) | Logging traffic to disk |
| [Mode 3: IDS / IPS](Operation%20Mode%203%3A%20IDS-IPS.md) | Detecting and blocking traffic with rules |
| [Mode 4: PCAP Investigation](Operation%20Mode%204%3A%20PCAP%20Investigation.md) | Analysing captured traffic offline |
| [Snort Rules](Snort%20Rules.md) | Rule syntax: header, options and examples |

## Quick example

```
alert icmp any any <> any any (msg: "ICMP packet detected"; sid: 100001; rev: 1;)
```

## About

Personal notes written while studying network security monitoring. Official docs: [snort.org](https://www.snort.org/documents)
