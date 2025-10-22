---
layout: post
title: Password Cracking 00
longtitle: Password Cracking - John the Ripper
tags:
- password cracking
- john the ripper
date: 2025-10-16
---

John the Ripper is an Open Source password security auditing and password recovery tool available for many operating systems.

## Download & Verify

[https://www.openwall.com/john/](https://www.openwall.com/john/)

Verify the download using the **GnuPG Keys** at [https://www.openwall.com/signatures/](https://www.openwall.com/signatures/)


> ##### Info
>
> This is already packaged in [Kali Linux](https://www.kali.org/get-kali/#kali-live)
>
{: .block-info}

## Usage 

Utilize [Hash Identification]({% link _posts/2025-10-16-Hash-Identifier.md %}) to identify the hash format.

```
john --list=formats | grep -iF '<PossibleFormat>'
```

With the `<Format>` identified, crack using:

```shell
john --wordlist=/usr/share/wordlist/rockyou.txt --format=<Format> <FullFilePath>
```

## Custom Rules

[https://www.openwall.com/john/doc/RULES.shtml](https://www.openwall.com/john/doc/RULES.shtml)

We are able to create Custom Rules for John the Ripper to utilize to account for password complexity requirements.

The Custom Rules will typically be written based on the information about the target.

## Wordlists

[Wordlists]({% link _posts/2025-10-16-Wordlists.md %})
