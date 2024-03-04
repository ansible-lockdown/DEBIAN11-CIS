# Debian 11 CIS

## Configure a Debian 11 machine to be [CIS](https://www.cisecurity.org/cis-benchmarks/) compliant

### Based on CIS Debian Linux 11 LTS Benchmark v1.0.0 [Release](https://downloads.cisecurity.org/#/)

![Org Stars](https://img.shields.io/github/stars/ansible-lockdown?label=Org%20Stars&style=social)
![Stars](https://img.shields.io/github/stars/ansible-lockdown/Debian11-cis?label=Repo%20Stars&style=social)
![Forks](https://img.shields.io/github/forks/ansible-lockdown/Debian11-cis?style=social)
![followers](https://img.shields.io/github/followers/ansible-lockdown?style=social)
[![Twitter URL](https://img.shields.io/twitter/url/https/twitter.com/AnsibleLockdown.svg?style=social&label=Follow%20%40AnsibleLockdown)](https://twitter.com/AnsibleLockdown)

![Discord Badge](https://img.shields.io/discord/925818806838919229?logo=discord)

![Release Branch](https://img.shields.io/badge/Release%20Branch-Main-brightgreen)
![Release Tag](https://img.shields.io/github/v/release/ansible-lockdown/Debian11-CIS)
![Release Date](https://img.shields.io/github/release-date/ansible-lockdown/Debian11-CIS)

[![Main Pipeline Status](https://github.com/ansible-lockdown/Debian11-CIS/actions/workflows/main_pipeline_validation.yml/badge.svg?)](https://github.com/ansible-lockdown/Debian11-CIS/actions/workflows/main_pipeline_validation.yml)

[![Devel Pipeline Status](https://github.com/ansible-lockdown/Debian11-CIS/actions/workflows/devel_pipeline_validation.yml/badge.svg?)](https://github.com/ansible-lockdown/Debian11-CIS/actions/workflows/devel_pipeline_validation.yml)
![Devel Commits](https://img.shields.io/github/commit-activity/m/ansible-lockdown/Debian11-CIS/devel?color=dark%20green&label=Devel%20Branch%20Commits)

![Issues Open](https://img.shields.io/github/issues-raw/ansible-lockdown/Debian11-CIS?label=Open%20Issues)
![Issues Closed](https://img.shields.io/github/issues-closed-raw/ansible-lockdown/Debian11-CIS?label=Closed%20Issues&&color=success)
![Pull Requests](https://img.shields.io/github/issues-pr/ansible-lockdown/Debian11-CIS?label=Pull%20Requests)

![License](https://img.shields.io/github/license/ansible-lockdown/Debian11-CIS?label=License)

---

## Looking for support?

[Lockdown Enterprise](https://www.lockdownenterprise.com#GH_AL_DEB11_cis)

[Ansible support](https://www.mindpointgroup.com/cybersecurity-products/ansible-counselor#GH_AL_DEB11_cis)

### Community

On our [Discord Server](https://www.lockdownenterprise.com/discord) to ask questions, discuss features, or just chat with other Ansible-Lockdown users

## Caution(s)

This role **will make changes to the system** that could break things. This is not an auditing tool but rather a remediation tool to be used after an audit has been conducted.

This role was developed against a clean install of the Operating System. If you are implimenting to an existing system please review this role for any site specific changes that are needed.

## Documentation

- [Read The Docs](https://ansible-lockdown.readthedocs.io/en/latest/)
- [Getting Started](https://www.lockdownenterprise.com/docs/getting-started-with-lockdown#GH_AL_DEB11_cis)
- [Customizing Roles](https://www.lockdownenterprise.com/docs/customizing-lockdown-enterprise#GH_AL_DEB11_cis)
- [Per-Host Configuration](https://www.lockdownenterprise.com/docs/per-host-lockdown-enterprise-configuration#GH_AL_DEB11_cis)
- [Getting the Most Out of the Role](https://www.lockdownenterprise.com/docs/get-the-most-out-of-lockdown-enterprise#GH_AL_DEB11_cis)

## Requirements

**General:**

- Basic knowledge of Ansible, below are some links to the Ansible documentation to help get started if you are unfamiliar with Ansible
  - [Main Ansible documentation page](https://docs.ansible.com)
  - [Ansible Getting Started](https://docs.ansible.com/ansible/latest/user_guide/intro_getting_started.html)
  - [Tower User Guide](https://docs.ansible.com/ansible-tower/latest/html/userguide/index.html)
  - [Ansible Community Info](https://docs.ansible.com/ansible/latest/community/index.html)
- Functioning Ansible and/or Tower Installed, configured, and running. This includes all of the base Ansible/Tower configurations, needed packages installed, and infrastructure setup.
- Please read through the tasks in this role to gain an understanding of what each control is doing. Some of the tasks are disruptive and can have unintended consiquences in a live production system. Also familiarize yourself with the variables in the defaults/main.yml file or the

**Technical Dependencies:**

- Running Ansible/Tower setup (this role is tested against Ansible version 2.9.1 and newer)
- Python3 Ansible run environment

## Auditing (new)

This can be turned on or off within the defaults/main.yml file with the variable run_audit. The value is false by default, please refer to the wiki for more details.

This is a much quicker, very lightweight, checking (where possible) config compliance and live/running settings.

A new form of auditing has been developed, by using a small (12MB) go binary called [goss](https://github.com/goss-org/goss) along with the relevant configurations to check. Without the need for infrastructure or other tooling.
This audit will not only check the config has the correct setting but aims to capture if it is running with that configuration also trying to remove [false positives](https://www.mindpointgroup.com/blog/is-compliance-scanning-still-relevant/) in the process.

Refer to [Debian11-CIS-Audit](https://github.com/ansible-lockdown/Debian11-CIS-Audit).

Further audit documentation can be found at [Read The Docs](https://ansible-lockdown.readthedocs.io/en/latest/)

## Role Variables

This role is designed that the end user should not have to edit the tasks themselves. All customizing should be done via the defaults/main.yml file or with extra vars within the project, job, workflow, etc.

## Branches

- **devel** - This is the default branch and the working development branch. Community pull requests will pull into this branch
- **main** - This is the release branch
- **reports** - This is a protected branch for our scoring reports, no code should ever go here
- **gh-pages** - This is the github pages branch
- **all other branches** - Individual community member branches

## Community Contribution

We encourage you (the community) to contribute to this role. Please read the rules below.

- Your work is done in your own individual branch. Make sure to Signed-off and GPG sign all commits you intend to merge.
- All community Pull Requests are pulled into the devel branch
- Pull Requests into devel will confirm your commits have a GPG signature, Signed-off, and a functional test before being approved
- Once your changes are merged and a more detailed review is complete, an authorized member will merge your changes into the main branch for a new release

## Pipeline Testing

uses:

- ansible-core 2.12
- ansible collections - pulls in the latest version based on requirements file
- runs the audit using the devel branch
- This is an automated test that occurs on pull requests into devel

## Added Extras

- [pre-commit](https://pre-commit.com) can be tested and can be run from within the directory

```sh
pre-commit run
```

## Known Issues

During rule 1.9 this may fail with the following

```bash
You must correct your GRUB install devices before proceeding:

      DEBIAN_FRONTEND=dialog dpkg --configure grub-pc
      dpkg --configure -a
```

Check your current settings

```bash
debconf-show grub-pc | grep install_devices:
```

If this returns the following with no value

```bash
* grub-pc/install_devices:
```

You need to set the device onto with grub-pc will configured

**USE AT YOUR OWN RISK**

Example only (be aware of disk):

Run the following with sudo:

```bash
disk=$(find /dev -type l -lname '*/sda' -path '*/by-id/*')
debconf-set-selections << EOF
grub-pc    grub-pc/install_devices    multiselect    $disk
EOF
apt update
apt install grub-pc -y
```

## Credits and Thanks

Massive thanks to the fantastic community and all its members.
This includes a huge thanks and credit to the original authors and maintainers.
