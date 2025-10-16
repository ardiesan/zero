---
title: YARA Rules
longtitle: YARA - Pattern Matching Swiss Army Knife
tags:
- threat hunt
- pattern matching
- yara rules
- malware research
date: 2025-10-09
layout: post
---

# YARA

**Y**et **A**nother **R**ecursive **A**cronym

**Threat Identification and Classification**

There are several rule security detection signatures which are key parts of threat detections and threat hunting.

YARA is a **tool** aimed at (but not limited to) helping malware researchers to 
*identify* and *classify* malware samples. With YARA you can create descriptions of
malware families (or whatever you want to describe) based on textual or binary 
patterns. Each description, a.k.a. *rule*, consists of a set of strings and a 
boolean expression which determine its logic.

It is the pattern matching switch army knife for malware researchers (and everyone else)

## Installation

The released files are compiled binaries specific to an operating system. Choose a release based on your Operating System.

[https://github.com/VirusTotal/yara/releases](https://github.com/VirusTotal/yara/releases)

> ##### Tip
> 
> Extract the Yara binaries in a path that you can add to your **PATH** variable.
>
{: .block-tip}

---

## YARA Rule

```
/*
    This is a multi-line comment ...
*/
rule silent_banker : banker // this is a single line comment. `: banker` is a tag
{
    meta:
        description = "This is just an example"
        threat_level = 3
        in_the_wild = true

    strings:
        $a = {6A 40 68 00 30 00 00 6A 14 8D 91}
        $b = {8D 4D B0 2B C1 83 C0 27 99 6A 4E 59 F7 F9}
        $c = "UVODFRYSIHLNWPEJXQZAKCBGMT"

    condition:
        $a or $b or $c
}
```

# Writing YARA Rules

[https://yara.readthedocs.io/en/latest/writingrules.html](https://yara.readthedocs.io/en/latest/writingrules.html)

---

# Running YARA

yara [options] *RULES* *TARGET*


i.e.:
```
yara [options] /path/to/yara-rule-or-directory-of-rules /path/of/target-file-or-directory
```

# YARA Extras

## Awesome Yara

A curated list of awesome YARA rules, tools, and resources.

[https://github.com/InQuest/awesome-yara](https://github.com/InQuest/awesome-yara)

## Yara Mail

A Python package and command line utility for scanning emails with YARA rules.

It is ideal for automated triage of phishing reports.

[https://github.com/VirusTotal/yara-python](https://github.com/VirusTotal/yara-python)
[https://pypi.org/project/yara-mail](https://pypi.org/project/yara-mail/)

> ##### Tip
>
> Using YARA with the Wazuh SIEM is an amazing free and fully operational combination.
>
{: .block-tip}
