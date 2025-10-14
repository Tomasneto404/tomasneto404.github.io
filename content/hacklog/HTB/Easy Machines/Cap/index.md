---
title: "Hack The Box | Easy Machines | Cap"
description: "How to Solve Cap Machine"
categories: ["walktroughs"]
tags: ["HTB", "Easy Machines", "Cap", "nmap", "gobuster", "wireshark", "ssh", "privesc", "linux", "enumeration", "flag" , "root"]
date: 2025-10-13
draft: false
image: "cap.png"
---

## Phase 1 - Information Gathering

## Phase 2 - Scanning / Discovery
Like every penetration test, we should start with the information-gathering phase. This stage is one of the most important, because it’s where we’ll uncover the majority of system vulnerabilities.
### nmap
Nmap is a Network tool that allows us to map the assets of a network.
```shell
nmap -sV -sC <target-ip> -oA nmapScans 
```
