---
title: Cryptography - GPG
longtitle: Introduction to Cryptography
date: 2025-10-08
categories:
- cryptography
tags:
- cryptography
- gpg
layout: post
permalink: /:categories/:title:output_ext
---


# Review of Hashing

Using one or all of the tools/command, get the hash of `juan.txt`
* `md5deep64`
* `certutil -hashfile`
* `Get-FileHash`
* `md5sum`

# Cryptography

Cryptography is the use of specialized codes and algorithms to _secure_ information,
making it _unreadable to unauthorized individuals_.

In law enforcement, it serves as a dual-edged sword: it's used to protect sensitive 
data and evidence, but it can also be used by criminals to _obfuscate_ or _encrypt_ 
their communications and digital evidence, creating a major challenge for investigations.

It is commonly used for secure communications to prevent eavesdroppers from listening,
and/or reading sensitive information.

*Keywords*

**secure**, **encrypted**, **obfuscated**, **authorized**

# Digital Signature

A digital signature is a cryptographic "fingerprint" used to _verify_ the 
_authenticity_ and _integrity_ of digital documents.

In law enforcement, it serves as a legally admissible method to prove that an 
electronic document, like an arrest warrant or evidence log, has not been tampered 
with and originated from a specific, _verified_ source.

*Keywords*

**verify**, **verified**, **authentic**, **authentication**, **integrity**, **untampered**, **non-repudiation**

---

Cryptography is the use of specialized codes and algorithms to _secure_ information,
making it _unreadable to unauthorized individuals_.

The process of communication in the presence of adversaries.

# Types of Cryptography

## 1. Symmetric-key

Uses a single, shared key for encryption and decryption.

#### Example - Caesar Cipher

https://cryptii.com/pipes/caesar-cipher


## 2. Asymmetric-key

Uses a pair of mathematically related keys - a **Public Key** for __encryption__ and a
**Private Key** for __decryption__.

#### Example 1 - Certificate Authorities

PNPKI - https://dict.gov.ph/pnpki

#### Example 2 - Decentralized PKI

DIDs (The Standard) - https://www.w3.org/TR/did-1.0/

#### Example 3 - Web of Trust

**PGP**, **OpenPGP**, **GnuPG**

https://www.progress.com/blogs/the-difference-between-pgp-openpgp-and-gnupg-encryption

---




# GPG - Web of Trust

- Microsoft Endorsement - https://learn.microsoft.com/en-us/system-center/orchestrator/standard-activities/pgp-encrypt-file
- Windows Installer - [https://www.gpg4win.org/get-gpg4win.htm](https://www.gpg4win.org/get-gpg4win.html)

## Tool Installation

Install **GPG4Win** using the Windows Install link above.

## Generate your KeyPair

Open `Terminal` on Windows, and go to `C:\cert-ph` directory.

```shell
gpg --full-generate-key
```

- Type or select `9` for `ECC (sign and encrypt)` functionality, & press enter
- Type or select `1` for `Curve 25519` ECC algorith, & press enter
- Type `1y` for `1 year` key duration/expiry, & press enter

---

## Identify your _KeyID_

```shell
gpg --list-keys --keyid-format long
```

>
> [keyboxd]
> ---------<br/><br/>
> pub   ed25519/_C317FBCB5B193D17_ 2025-09-26 [SC] [expires: 2026-09-26]
>       F9603BC8A86CC5EE8CBBD2FBC317FBCB4B170D17
> uid                 [ultimate] Juan de la Cruz <jdelacruz@example.net>
> sub   cv25519/CE719CFDB2DD0736 2025-09-26 [E] [expires: 2026-09-26]
> 


---

## Extract your _Public Key_

```shell
gpg --armor --export {KeyID} 
```

> -----BEGIN PGP PUBLIC KEY BLOCK-----
> <br/> 
> mENFaNadhBYJKwYBBAHaRw8BAQdA0NQHsKJBpXrDy6DC2n01LLOi6R1m3vo4QKTI
> oKLiI4m0KlJheW1vbmQgT2xhdmlkZXMgPGFyZGllb2xhdmlkZXNAZ21haWwuY29t
> PoiZBBMWCgBBFiEE+WA82Khsxe6Mu9L7wxf7y1sXDRcFAmjWnYQCGwMFCQHhM4AF
> CwkIBwICIgIGFQoJCAsCBBYCAwECHgcCF4AACgkQwxf7y1sXDRd2jAEAg6H4JKwh
> ZA+l8YyMXmCveNO6QWsTWFK63kHi+rj31q8BAPENOSGUcMugobzmEkeqogItrgjY
> hOfQmKx5XASwfIgFuDgEaNadhBIKKwYBBAGXVQEFAQEHQL88J9B5Bf9XrZYAivia
> 1Ek9gO6Tn7JgYkSB70/tqDB7AwEIB4h+BBgWCgAmFiEE+WA82Khsxe6Mu9L7wxf7
> y1sXDRcFAmjWnYQCGwwFCQHhM4AACgkQwxf7y1sXDRezpgD/TI98JZMGtZeklb2U
> Wew7J8trhkKHXrPZvkHgXcZ77skBAOaxnPflXm8Pf4tpcT7Nh4Fi1G9G5fmKYk08
> u2Bj9z8P
> =6GHj
> -----END PGP PUBLIC KEY BLOCK-----

## Extract your _Public Key_ to a File

```shell
gpg --armor --export {KeyID} > name.asc 
```

---

# Activity

## Activity 1

**_ESTABLISHING YOUR WEB_: Personal Emails**

1. Group yourselves into `4`, trusted buddies
2. Share to each other your personal emails  
3. Email to one another your _Public Key_, or your `.asc` file.

**_LOCAL WEB OF TRUST_: Your Trusted Keys**

1. Download the _Public Key_ shared to you.
2. Import to your _Web of Trust<br/><br/>_
```shell
gpg -i jdelacruz.asc
```

**_CHECK TRUSTED KEYS_: Verify**

1. Verify that the trusted key has been imported correctly.<br/><br/>
```
gpg --list-keys --keyid-format long
```

---

## Activity 2

**_ENCRYPTING MESSAGES_: Messages & Trusted Recipient**

1. Write down any sample message (non-sensitive) to a text file
2. Encrypt the text file., and set intended recipient to you and 2 of your groupmate.<br/><br/>
```shell
gpg -sea -r {KeyID} -r {Recipient_KeyID} file.ext 
```
3. The command above will create a file `file.ext.asc`
4. Email the file `file.ext.asc` to everyone on your group. 

---

## Activity 3

**_DECRYPTING MESSAGES_: Only Trusted Can Decrypt**

1. Once you receive an email with encrypted attachment, download the attachment, and decrypt.<br/><br/>
```shell
gpg -d file.ext.asc
```
---

**_ENCRYPTING LARGE FILES_**

1. Encrypt the file. With a detached signature; `-b` option<br/><br/>
```shell
gpg -bes -r {KeyID} -r {Recipient_KeyID} large_file.ext 
```
2. The command above will create a file `large_file.ext.asc`, this is the `signature_file`
3. If uploading on a hosting service, be sure to upload the `large_file.ext.asc` for recipient to validate the decryption 

Note: `large_file` should be the filename of your file. and `ext` is the extension of your file.

**_DECRYPTING FILES_**

1. Verify & Decrypt<br/><br/>
```shell
gpg --version large_file.ext.asc large_file.ext
```

---

> ##### Info
> 
> The above commands will allow one to establish Confidentiality and Integrity of a file or data. 
> The Availability of the public keys will discussed in a separated material.
>
{: .block-info}
