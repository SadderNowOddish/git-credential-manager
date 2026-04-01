# Git Credential Manager

[![Build Status][build-status-badge]][workflow-status]

---

[Git Credential Manager][gcm] (GCM) is a secure
[Git credential helper][git-credential-helper] built on [.NET][dotnet] that runs
on Windows, macOS, and Linux. It aims to provide a consistent and secure
authentication experience, including multi-factor auth, to every major source
control hosting service and platform.

GCM supports (in alphabetical order) [Azure DevOps][azure-devops], Azure DevOps
Server (formerly Team Foundation Server), Bitbucket, GitHub, and GitLab.
Compare to Git's [built-in credential helpers][git-tools-credential-storage]
(Windows: wincred, macOS: osxkeychain, Linux: gnome-keyring/libsecret), which
provide single-factor authentication support for username/password only.

GCM replaces both the .NET Framework-based
[Git Credential Manager for Windows][gcm-for-windows] and the Java-based
[Git Credential Manager for Mac and Linux][gcm-for-mac-and-linux].

## Install

See the [installation instructions][install] for the current version of GCM for
install options for your operating system.

## Current status

Git Credential Manager is currently available for Windows, macOS, and Linux\*.
GCM only works with HTTP(S) remotes; you can still use Git with SSH:

- [Azure DevOps SSH][azure-devops-ssh]
- [GitHub SSH][github-ssh]
- [Bitbucket SSH][bitbucket-ssh]

Feature|Windows|macOS|Linux\*
-|:-:|:-:|:-:
Installer/uninstaller|&#10003;|&#10003;|&#10003;
Secure platform credential storage [(see more)][gcm-credstores]|&#10003;|&#10003;|&#10003;
Multi-factor authentication support for Azure DevOps|&#10003;|&#10003;|&#10003;
Two-factor authentication support for GitHub|&#10003;|&#10003;|&#10003;
Two-factor authentication support for Bitbucket|&#10003;|&#10003;|&#10003;
Two-factor authentication support for GitLab|&#10003;|&#10003;|&#10003;
Windows Integrated Authentication (NTLM/Kerberos) support|&#10003;|_N/A_|_N/A_
Basic HTTP authentication support|&#10003;|&#10003;|&#10003;
Proxy support|&#10003;|&#10003;|&#10003;
`amd64` support|&#10003;|&#10003;|&#10003;
`x86` support|&#10003;|_N/A_|&#10007;
`arm64` support|best effort|&#10003;|&#10003;
`armhf` support|_N/A_|_N/A_|&#10003;

(\*) GCM guarantees support only for [the Linux distributions that are officially
supported by dotnet][dotnet-distributions].

## Supported Git versions

Git Credential Manager tries to be compatible with the broadest set of Git
versions (within reason). However there are some known problematic releases of
Git that are not compatible.

- Git 1.x

  The initial major version of Git is not supported or tested with GCM.

- Git 2.26.2

  This version of Git introduced a breaking change with parsing credential
  configuration that GCM relies on. This issue was fixed in commit
  [`12294990`][gcm-commit-12294990] of the Git project, and released in Git
  2.27.0.

## How to use

Once it's installed and configured, Git Credential Manager is called implicitly
by Git. You don't have to do anything special, and GCM isn't intended to be
called directly by the user. For example, when pushing (`git push`) to
[Azure DevOps][azure-devops], [Bitbucket][bitbucket], or [GitHub][github], a
window will automatically open and walk you through the sign-in process. (This
process will look slightly different for each Git host, and even in some cases,
whether you've connected to an on-premises or cloud-hosted Git host.) Later Git
commands in the same repository will re-use existing credentials or tokens that
GCM has stored for as long as they're valid.

Read full command line usage [here][gcm-usage].

### Configuring a proxy

See detailed information [here][gcm-http-proxy].

## Additional Resources

See the [documentation index][docs-index] for links to additional resources.

## Experimental Features

- [Windows broker (experimental)][gcm-windows-broker]

## Future features

Curious about what's coming next in the GCM project? Take a look at the [project
roadmap][roadmap]! You can find more details about the construction of the
roadmap and how to interpret it [here][roadmap-announcement].

## Contributing

This project welcomes contributions and suggestions.
See the [contributing guide][gcm-contributing] to get started.

This project follows [GitHub's Open Source Code of Conduct][gcm-coc].

## License

We're [MIT][gcm-license] licensed.
When using GitHub logos, please be sure to follow the
[GitHub logo guidelines][github-logos].

[azure-devops]: https://azure.microsoft.com/en-us/products/devops
[azure-devops-ssh]: https://docs.microsoft.com/en-us/azure/devops/repos/git/use-ssh-keys-to-authenticate?view=azure-devops
[bitbucket]: https://bitbucket.org
[bitbucket-ssh]: https://confluence.atlassian.com/bitbucket/ssh-keys-935365775.html
[build-status-badge]: https://github.com/git-ecosystem/git-credential-manager/actions/workflows/continuous-integration.yml/badge.svg
[docs-index]: https://github.com/git-ecosystem/git-credential-manager/blob/release/docs/README.md
[dotnet]: https://dotnet.microsoft.com
[dotnet-distributions]: https://learn.microsoft.com/en-us/dotnet/core/install/linux
[git-credential-helper]: https://git-scm.com/docs/gitcredentials
[gcm]: https://github.com/git-ecosystem/git-credential-manager
[gcm-coc]: CODE_OF_CONDUCT.md
[gcm-commit-12294990]: https://github.com/git/git/commit/12294990c90e043862be9eb7eb22c3784b526340
[gcm-contributing]: CONTRIBUTING.md
[gcm-credstores]: https://github.com/git-ecosystem/git-credential-manager/blob/release/docs/credstores.md
[gcm-for-mac-and-linux]: https://github.com/microsoft/Git-Credential-Manager-for-Mac-and-Linux
[gcm-for-windows]: https://github.com/microsoft/Git-Credential-Manager-for-Windows
[gcm-http-proxy]: https://github.com/git-ecosystem/git-credential-manager/blob/release/docs/netconfig.md#http-proxy
[gcm-license]: LICENSE
[gcm-usage]: https://github.com/git-ecosystem/git-credential-manager/blob/release/docs/usage.md
[gcm-windows-broker]: https://github.com/git-ecosystem/git-credential-manager/blob/release/docs/windows-broker.md
[git-tools-credential-storage]: https://git-scm.com/book/en/v2/Git-Tools-Credential-Storage
[github]: https://github.com
[github-ssh]: https://help.github.com/en/articles/connecting-to-github-with-ssh
[github-logos]: https://github.com/logos
[install]: https://github.com/git-ecosystem/git-credential-manager/blob/release/docs/install.md
[ms-package-repos]: https://packages.microsoft.com/repos/
[roadmap]: https://github.com/git-ecosystem/git-credential-manager/milestones?direction=desc&sort=due_date&state=open
[roadmap-announcement]: https://github.com/git-ecosystem/git-credential-manager/discussions/1203
[workflow-status]: https://github.com/git-ecosystem/git-credential-manager/actions/workflows/continuous-integration.yml
# GitHub SIRT description RFC 2350

<!-- markdownlint-disable search-replace -->

## 1. Document Information

TLP:CLEAR

### 1.1 Date of Last Update

Version 1.02, updated 2025-12-18.

### 1.2 Distribution List for Notifications

There is no distribution list for changes to this document.

### 1.3 Locations where this Document May Be Found

The current version of this document may be found at:

<https://docs.github.com/site-policy/security-policies/github-sirt-description-rfc-2350>

## 2. Contact Information

### 2.1 Name of the Team

GitHub Security Incident Response Team (SIRT)

Subteams:

* Corporate Security Incident Response Team (CSIRT)
* Product Security Incident Response Team (PSIRT)
* Bug Bounty

### 2.2 Address

GitHub SIRT
88 Colin P. Kelly Jr. St.
San Francisco, CA 94107
United States

### 2.3 Time Zone

Our team mainly works in the contiguous United States and keeps to these hours:

* EST/EDT
* CST/CDT
* MST/MDT
* PST/PDT

### 2.4 Telephone Number

None available.

### 2.5 Facsimile Number

None available.

### 2.6 Other Telecommunication

None available.

### 2.7 Electronic Mail Address

security(at)github(dot)com

This relays email to the human(s) on duty for GitHub SIRT.

### 2.8 Public Keys and Encryption Information

GitHub SIRT has a PGP public key:

* Key ID: `B0614CADF0EAF85433C715A508F419AA6FB92A90`
* Key expiry: `2027-12-18`

```text
-----BEGIN PGP PUBLIC KEY BLOCK-----

mDMEaURZwxYJKwYBBAHaRw8BAQdAg7ZWj5TyaA/C590af0ldWITh7zd8Z17NYH0f
7FGKcLe0JUdpdEh1YiBTZWN1cml0eSA8c2VjdXJpdHlAZ2l0aHViLmNvbT6ImQQT
FgoAQRYhBLBhTK3w6vhUM8cVpQj0GapvuSqQBQJpRFnDAhsDBQkDwmcABQsJCAcC
AiICBhUKCQgLAgQWAgMBAh4HAheAAAoJEAj0GapvuSqQlLkBANp/JNGXDOIkQL8J
Fwmhr+ITQ1gudJtf29GS8h05jm9iAQCoEiDUQLgngX/qxjT0OEdTXjYk39JGItNE
klI0rrZzCLg4BGlEWcMSCisGAQQBl1UBBQEBB0A+yeNKyL9TqzHVzo4yksCfOiDo
Y7bbI9gr1a/LAIRaKQMBCAeIfgQYFgoAJhYhBLBhTK3w6vhUM8cVpQj0GapvuSqQ
BQJpRFnDAhsMBQkDwmcAAAoJEAj0GapvuSqQnOMA/ik/dvObq/da3zEbRt90Z10p
A5CG9QOixXSNJ7Jj6DIlAQChy/9nM6olIwmoBl8x0FtZoqzYxFcocLxFElJfk0tk
Cw==
=yWk0
-----END PGP PUBLIC KEY BLOCK-----
```

### 2.9 Team Members

The list of team members is not publicly available.

### 2.10 Other Information

None available.

### 2.11 Points of Customer Contact

Vulnerabilities should be reported to our bug bounty program:

<https://bounty.github.com>

GitHub customers should contact their account manager or GitHub Support for first level support and escalations:

<https://support.github.com>

Other security related communications can be directed to our email address detailed in Section 2.7.

## 3. Charter

### 3.1 Mission Statement

GitHub is committed to maintaining the confidentiality, integrity, and availability of both its platform and the intellectual property and personal information of its users, customers, and employees. In order to ensure these principles are upheld, GitHub maintains robust vulnerability management, incident response, and threat hunting capabilities.

### 3.2 Constituency

Our constituency is any individual or organization that uses a GitHub product or service, as well as GitHub employees, contractors, and GitHub Inc.

Some examples of GitHub products and services are:

* GitHub.com
* GitHub Enterprise Server
* GitHub Actions
* GitHub Desktop
* GitHub CLI
* GitHub API
* npm <!-- markdownlint-disable-line GHD034 -->

### 3.3 Sponsorship and/or Affiliation

GitHub SIRT is a team within GitHub. Funding is provided by GitHub.

### 3.4 Authority

GitHub SIRT operates under the authority of the Chief Information Security Officer of GitHub.

## 4. Policies

### 4.1 Types of Incidents and Level of Support

GitHub SIRT is authorized to address all types of computer security incidents which occur, or threaten to occur, within its constituency.

The level of support depends on the type and severity of the given security incident, the number of affected entities within our constituency, and our resources at the time.

### 4.2 Co-operation, Interaction and Disclosure of Information

GitHub SIRT takes every effort to safely and securely share information with affected parties during incident response situations while respecting the privacy and trust of our constituents.

### 4.3 Communication and Authentication

GitHub SIRT makes use of the Traffic Light Protocol (TLP) for information sharing.

Email is the preferred method of communication. All sensitive information should be encrypted using the GitHub SIRT PGP key (as detailed in Section 2.8) prior to sending.

## 5. Services

### 5.1 Incident Response

GitHub SIRT is responsible for incident response internally at GitHub where at least one member of the constituency is affected.

GitHub SIRT does not provide incident response services for customers. Every effort is made to provide timely and accurate information during security incidents to affected customers so they can conduct their own investigations and respond appropriately. See section 2.11 for customer points of contact.

#### 5.1.1 Incident Triage

GitHub SIRT carries out the following activities for incident triage:

* Security signals are collected and interpreted to determine risk, severity, and priority.
* Investigation as to whether an incident occurred and what its effect and impact was.

This list is not exhaustive.

#### 5.1.2 Incident Coordination

GitHub SIRT carries out the following activities for incident coordination:

* Situational awareness and analysis for stakeholders such as engineering, legal, and support teams.
* Command role with authority to direct resources as required.
* External coordination with affected or involved third-parties.

This list is not exhaustive.

#### 5.1.3 Incident Resolution

GitHub SIRT carries out the following activities for incident resolution:

* Engages relevant internal teams to eradicate, restore, and secure.
* Collection and storage of evidence for internal use as well as potential law enforcement involvement.
* Notification to affected constituents.
* Postmortem authoring with lessons learned and post-incident repair items.

This list is not exhaustive.

### 5.2 Proactive Activities

GitHub SIRT develops, maintains, and operates threat hunting and detection tools and techniques to proactively identify risks and threats.

Work is also done on education, preparation, workflow development, and community outreach.

## 6. Incident Reporting Forms

None available. Please review Section 2.11 for reporting guidance.

## 7. Disclaimers

While every precaution will be taken in the preparation of information, notifications and alerts, GitHub SIRT assumes no responsibility for errors or omissions, or for damages resulting from the use of the information contained within.
