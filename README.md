# MailAD
<!-- ALL-CONTRIBUTORS-BADGE:START - Do not remove or modify this section -->
[![All Contributors](https://img.shields.io/badge/all_contributors-4-orange.svg?style=flat-square)](#contributors-)
<!-- ALL-CONTRIBUTORS-BADGE:END -->

This is a handy tool to provision a mail server on linux linked to an Active Directory server (Samba or Windows, it does not care) with some constraints in mind, as this is a typical mail config to be used in Cuba under certain laws and security requirements.

## Rationale

This repository is intended to be cloned on your fresh OS install under `/root` (you can use a LXC instance, VM, CT, etc) and setup on a main conf file as per the file comments, then run the steps on a makefile and follow the steps to configure your server.

After a few steps you will have a mail server up and running in about 15 minutes tops. _(this time is based on a 2Mbps internet connection to a repository, if you have a local repository it will be less)_

This tool is tested and supported on:

- Ubuntu Bionic 18.04 (former LTS).
- Ubuntu Focal 20.04 (actual LTS and actual dev env).
- Debian Buster 10 (see note below please).

_**Note:** If you are using a Debian Buster Container on LXC (Proxmox for example) you need to tweak the dovecot install or it will not work, see [this fix](https://serverfault.com/questions/976250/dovecot-lxc-apparmor-denied-buster) for more info_

It's recommended that the instance of MailAD sits inside your DMZ net with a firewall between it and your users and a mail gateway like [Proxmox Mail Gateway](https://www.proxmox.com/en/proxmox-mail-gateway) between it and the outside world.

## Features

This will provision a mail server in a enterprise as a real server facing the users, you can see the major features in the [Features.md](Features.md) file, among others you will find:

0. Low resource footprint.
0. Advanced (and optional) mail filtering features that includes attachments, SPF, AntiVirus & Spam.
0. Daily mail traffic summary in you inbox.
0. Encrypted LDAP communication as an option.
0. In place protection to major and known SSL & mail services attacks.
0. Optional user privilege access via AD groups (local/national/international).
0. Automatic alias using AD groups.
0. Optional disclaimer/notice/adverting on every outgoing mail.
0. Manual alias, manual ban, manual headers & body checks.
0. On demand Backup and restore of raw configurations.
0. Painless upgrades (Really!).

## TODO

There is a [TODO list](TODO.md), a kind of "roadmap" for new features, but as I (only one dev so far) have a life, a family and a daily job, you know...

All dev is made on weekend or late at night (seriously take a peek on the commit dates!) if you need a feature or fix ASAP, please take into account making a donation or found me and I will be happy to help you ASAP, my contact info is on the bottom of this page.

## Constraints and requirements

Remember the comment at top of the page about _"...with some constraints in mind..."_ yeah, here they are:

0. Your user base and config came from an Active Directory (AD from now on) as mentioned, we prefer a Samba AD but works on Windows too; see [AD requirements for this tool](AD_Requirements.md)
0. The mail storage will be a folder in `/home/vmail`, all mail will belong to a user named `vmail` with uid:5000 & gid:5000. Tip: that folder can be a NFS mount or any other type of network storage (configurable)
0. You use a Windows PC to control and manage the domain (must be a domain member and have the RSAT installed and activated), we recommend a Windows 10 LTSC/Professional
0. The server allows all communications protocols by default _(POP3, POP3S, IMAP, IMAPS, SMTP, SSMTP and SUBMISSION)_ it's **up to you** to restrict the users access in a way that them just use the secure versions (POP3S, IMAPS & SUBMISSION. Take into account that the SMTP service must be used only to send/receive the emails from the outside world)

## How to install or try it?

We have a [INSTALL.md](INSTALL.md) file just for that, and also a [FAQ](FAQ.md) file with common problems.

## This is free software!

Have a comment, question, contributions or fix?

Use the Issues tab in the repository URL or drop me a message via [Twitter](https://twitter.com/co7wt) or [Telegram](https://t.me/pavelmc)

We have a [file to register the contributions](Contributors.md) to this Software.

## Contributors ✨

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="https://github.com/danny920825"><img src="https://avatars2.githubusercontent.com/u/33090194?v=4" width="100px;" alt=""/><br /><sub><b>danny920825</b></sub></a><br /><a href="https://github.com/stdevPavelmc/mailad/commits?author=danny920825" title="Tests">⚠️</a> <a href="#ideas-danny920825" title="Ideas, Planning, & Feedback">🤔</a></td>
    <td align="center"><a href="https://github.com/HugoFlorentino"><img src="https://avatars0.githubusercontent.com/u/11479345?v=4" width="100px;" alt=""/><br /><sub><b>HugoFlorentino</b></sub></a><br /><a href="#ideas-HugoFlorentino" title="Ideas, Planning, & Feedback">🤔</a> <a href="#example-HugoFlorentino" title="Examples">💡</a></td>
    <td align="center"><a href="https://www.sysadminsdecuba.com"><img src="https://avatars1.githubusercontent.com/u/12705691?v=4" width="100px;" alt=""/><br /><sub><b>Armando Felipe</b></sub></a><br /><a href="#ideas-armandofcom" title="Ideas, Planning, & Feedback">🤔</a></td>
    <td align="center"><a href="https://github.com/Koratsuki"><img src="https://avatars0.githubusercontent.com/u/20727446?v=4" width="100px;" alt=""/><br /><sub><b>Koratsuki</b></sub></a><br /><a href="#ideas-Koratsuki" title="Ideas, Planning, & Feedback">🤔</a> <a href="https://github.com/stdevPavelmc/mailad/commits?author=Koratsuki" title="Code">💻</a></td>
  </tr>
</table>

<!-- markdownlint-enable -->
<!-- prettier-ignore-end -->
<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!