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
Esta é a primeira etapa quando se performa um <i>pentest</i>. É aqui que se recolhe informações sobre o nosso alvo (domínios, IPs, serviços, pessoas, tecnologias, ...) para nos ajudar a construir um mapa da superfície de ataque.
Bem, isto é apenas uma máquina do <i>Hack The Box</i> por isso vamo-nos focar apenas no IP que nos deram. Neste caso o alvo tinha o IP 10.10.10.245
## Phase 2 - Scanning / Discovery
Like every penetration test, we should start with the information-gathering phase. This stage is one of the most important, because it’s where we’ll uncover the majority of system vulnerabilities.
### nmap
Nmap is a Network tool that allows us to map the assets of a network.
```shell
nmap -sV -sC <target-ip> -oA nmapScans 
```
- -sV - Faz um <i>scan<i> por serviços ativos e respetivas versões
- -sC - Ativa <i>scripts</i> "padrão" que fazem reconhecimento aprofundado sobre serviços (banners, títulos HTTP, certificados SSL, ...)
- -oA - Guarda o resultado em todos os formatos no ficheiro especificado
- nmapScans - Nome para dar aos ficheiros com o resultado do nmap

Obteve-se o seguinte resultado:

```shell
Starting Nmap 7.95 ( https://nmap.org ) at 2025-09-27 14:50 EDT
Nmap scan report for 10.10.10.245
Host is up (0.087s latency).
Not shown: 997 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.2 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 fa:80:a9:b2:ca:3b:88:69:a4:28:9e:39:0d:27:d5:75 (RSA)
|   256 96:d8:f8:e3:e8:f7:71:36:c5:49:d5:9d:b6:a4:c9:0c (ECDSA)
|_  256 3f:d0:ff:91:eb:3b:f6:e1:9f:2e:8d:de:b3:de:b2:18 (ED25519)
80/tcp open  http    Gunicorn
|_http-title: Security Dashboard
|_http-server-header: gunicorn
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 16.09 seconds
```