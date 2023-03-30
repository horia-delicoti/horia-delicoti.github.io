---
title: "Pickle Rick: Try Hack Me Walkthrough"
subtitle: "A Rick and Morty CTF. Help turn Rick back into a human!"
date: 2023-01-22T11:06:41+03:00
draft: false

tags: [tryhackme]
categories: []
ontawesome: true
linkToMarkdown: true
rssFullText: false
---

Pickle Rick is a CTF challenge vulnerable VM from Try Hack Me.

# Information Gathering

Let’s start with a nmap scan to establish the open ports in the host

```sh
# nmap -sC -sV -oN nmap/initial 10.10.195.247
...
Nmap scan report for 10.10.195.247
Host is up (0.086s latency).
Not shown: 997 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.6 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   2048 43fb183b5a7f980f8c157d6af45eaf35 (RSA)
|   256 da74782db61daab73e657f0b737b9297 (ECDSA)
|_  256 3128da998fc9fc3c56c5a606ccd2b377 (ED25519)
53/tcp open  domain?
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Rick is sup4r cool
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```