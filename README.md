<img src="/project-logo.png" align="left" width="192px" height="192px"/>
<img align="left" width="0" height="192px" hspace="10"/>

> Installation documentation for Passbolt CE using AWS AMI
[![Under Development](https://img.shields.io/badge/under-development-orange.svg)](https://github.com/cez-aug/github-project-boilerplate) [![Public Domain](https://img.shields.io/badge/public-domain-lightgrey.svg)](https://creativecommons.org/publicdomain/zero/1.0/) [![Travis](https://img.shields.io/travis/cez-aug/github-project-boilerplate.svg)](http://github.com/cez-aug/github-project-boilerplate)

> This repo is to serve as documentation of my installation, configuration, troubleshooting, and remediation of issues installing the Passbolt CE password manager. I used the Passbolt provided AWS AMI to install, only deviating where noted further in this document.
<br>
<br>

# Getting Started

> **[!!]** If you're migrating from another password manager, ensure that you are exporting to a KeePass .kdbx or LastPass .csv format

Following the instructions outlined in the Passbolt documentation, I was able to get the instance up and running. To stay within the limits of AWS Free Tier, I opted to set the **instance type** to *t2.micro*.
* The t2.micro tier has worked flawlessly in day to day use. However, I ran in to one issue while importing my passwords (see [Issues](issues.md)).

## To-Do

- [ ] Add page documenting the creation of Lambda EC2Start & EC2Stop automations

## Acknowledgements

* [Passbolt Installation Guide](https://help.passbolt.com/hosting/install/ce/aws.html)
* [Passbolt Forums - LetsEncrypt Issue](https://community.passbolt.com/t/not-able-to-install-passbolt-ce-on-ubuntu-20-04-with-lets-encrypt/4168)