---
layout: post
title: Cryptography - Kleopatra
longtitle: Cryptography - Kleopatra  
categories:
- cryptography
tags:
- encrypted messages
date: 2025-10-09
permalink: /:categories/:title:output_ext
---

<style type="text/css">
figure { display: inline-block; margin-bottom: 30px; }
figure img { vertical-align: top; }
.markdown-section figure figcaption, figure figcaption { text-align: center; font-size: 0.9em !important; }
</style>

> ##### Info
>
> Kleopatra uses [GPG]({% link _posts/2025-10-08-Introduction-to-Cryptography.md %}) as its backend.
> Most if not all that you can do cryptographically with Kleopatra can de done using the command `gpg`
>
{: .block-info}

Kleopatra is a certificate manager and graphical user interface (GUI) for GnuPG. The software stores your OpenPGP certificates and keys. It is available for Windows and Linux.

[https://apps.kde.org/kleopatra/](https://apps.kde.org/kleopatra/) is its official home page.

For Windows, you can download it as part of Gpg4win package at [https://gpg4win.org/download.html](https://gpg4win.org/download.html)

## Setup an Assymetric Key

> ##### Info
>
> Only the location of the title, minimize, maximize, and close buttons naturally vary between operating systems. 
> Most of the GUI buttons will be where they are in the section of the GUI in Windows as well as with MacOS and Linux.
>
{: .block-info}

### Start - Empty Certificates

In most cases, you will start with an empty Certificates setup. This will be populated already if you have setup GPG keys via command line or terminal.

<figure>
<img alt="Starting - Empty Keys" src="{{ site.baseurl }}/assets/images/kleopatra/01.png" />
<figcaption>Fig. 1 - Starting - Empty Keys</figcaption>
</figure>

> ##### Tip
> 
> Note that our Kleopatra screenshot above starts with the "Certificate" tab. If yours is not in that tab, click "Certificates" to make following this guide easier.
>
{: .block-tip}

### New OpenPGP Key Pair

Alt+F > New OpenPGP Key Pair (Ctrl+N) will open up dialog which will guide you in the setup.

<figure>
<img alt="New OpenPGP Key Pair Menu" src="{{ site.baseurl }}/assets/images/kleopatra/02.png" />
<figcaption>Fig. 2 - New OpenPGP Key Pair Menu</figcaption>
</figure>


### Key Pair Information

In our brief introduction to Cryptography, Assymetric Keys requires and/or generates a Private and Public Key.

The Public Key are the key you need to distribute to trusted individuals or to a central trusted key server.

While the Private Key should never be in the hands of anyone other than you. As such the information you put in the dialog below are information about you and a symmetric key to add an extra layer of security to your private key.

**Ensure that "Protect Generated Key with a Passphrase" is checked.**

<figure>
<img src="{{ site.baseurl }}/assets/images/kleopatra/03.png" alt="Key Pair Information" />
<figcaption>Fig. 3 - Key Pair Information</figcaption>
</figure>


### Two-Factor

The Private Key is something that you have, while the Passphrase is something that you know. This makes the setup two-factor protected.

<figure>
<img alt="Two-Factor" src="{{ site.baseurl }}/assets/images/kleopatra/04.png" />
<figcaption>Fig. 4 - Two-Factor</figcaption>
</figure>


### Success!

You will see a similar dialog below once the generation succeeds.

> ##### Warning
>
> It is impossible to recover the Private Key or use it if you forget the passphrase.
> Don't write the passphrase anywhere, but make sure you remember it.
>
{: .block-warning}

<figure>
<img alt="Key Generation Successful" src="{{ site.baseurl }}/assets/images/kleopatra/05.png" />
<figcaption>Fig. 5 - Key Generation Successful</figcaption>
</figure>


### Populated Kleopatra

> ##### Info
>
> You now have a Private Key with which you can sign and encrypt files or documents.
>
{: .block-info}

<figure>
<img alt="Populated Kleopatra" src="{{ site.baseurl }}/assets/images/kleopatra/06.png" />
<figcaption>Fig. 6 - Key now available</figcaption>
</figure>

---

## Signing Files

Signing a file with **OpenPGP** or **GnuPG** is a cryptographic process that uses a **private key** to generate a digital **signature** for a specific file.

The primary purposes of signing a file are **authentication** and **integrity**:

### Authentication (Who Signed It)
The signature verifies the **identity** of the signer. Anyone with the signer's corresponding **public key** can verify that the signature was created by the holder of the matching private key. It proves the file genuinely came from the person or entity claiming to be the sender.


### Integrity (Has It Been Changed)

The signature assures that the file **hasn't been tampered with** since it was signed. The signature is essentially a cryptographic hash of the file that's encrypted with the private key. If even a single bit in the file is changed after signing, the verification process using the public key will fail, indicating the file's content is no longer the same as when it was signed.

### Technical Process Overview

1.  **Hashing**: A cryptographic **hash function** (like SHA-256) is applied to the file's content, generating a fixed-size, unique **message digest** (or hash).
2.  **Encryption (The Signature)**: The sender uses their **private key** to encrypt this message digest. This encrypted digest is the **digital signature**.
3.  **Distribution**: The original file and the newly created digital signature are typically sent together.
4.  **Verification**: The recipient uses the signer's **public key** to decrypt the signature, retrieving the original message digest. They then independently hash the received file's content and compare their new hash with the decrypted hash. If the two hashes **match**, the signature is valid, confirming the identity and integrity of the file.

### Analogy
Signing a file is similar to sealing a physical document with a personalized, tamper-evident wax seal and a unique signet ring:

* **Signet Ring (Private Key)**: Only the owner has this. It creates the unique mark.
* **Wax Seal (Digital Signature)**: The mark itself.
* **Inspecting the Mark (Public Key Verification)**: Others can examine the seal to confirm it was made by that specific ring and that the wax is unbroken, ensuring the document inside is genuine and hasn't been opened.

### Practical Signing

Click "Sign/Encrypt" button. Look at the screenshot below to follow along.

<figure>
<img alt="Signing" src="{{ site.baseurl }}/assets/images/kleopatra/07.png" />
<figcaption>Fig. 7 - Sign/Encrypt Files/Documents</figcaption>
</figure>


#### Select, Sign, and/or Encrypt 

In the screenshot below, you can select one or more file to sign and/or encrypt.

<figure>
<img alt="File Selection Dialog" src="{{ site.baseurl }}/assets/images/kleopatra/08.png" />
<figcaption>Fig. 8 - Select One or More Files to Sign and/or Encrypt</figcaption>
</figure>

After selecting one or more files, the following dialog will be presented to you:

<figure>
<img alt="Signing" src="{{ site.baseurl }}/assets/images/kleopatra/09.png" />
<figcaption>Fig. 9 - Select one or more files to Sign/Encrypt</figcaption>
</figure>

##### Sign

If you are only signing document/s, uncheck all under the "Encrypt" section. Examine **Fig. 9** to understand what to do.

##### Encrypt

If you are encrypting document/s, ensure that "Encrypt for me" is checked. And that you have already imported the Public Key of the person you are encrypting a document for.

