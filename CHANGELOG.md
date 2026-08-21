# Changes to DEB11CIS

## Based on CIS V2.0.0 - Aug26 Updates

- Readme updated and aligned
- workflows actions bumped version
- README updates and updated contributing and contributors

### Benchmark alignment to v2.0.0

- Renumbered System Auditing section from 6.3.x to 6.4.x to match the benchmark - 39 controls
  across tasks, defaults, vars/main.yml, vars/is_container.yml, prelim.yml and templates
- Task titles synced to benchmark wording for 1.1.2.6.1, 1.1.2.7.1, 1.3.1.3, 1.5.4, 1.6.2,
  1.6.3, 2.1.6, 5.3.3.3.1, 5.4.1.1, 5.4.1.5, 6.4.1.1, 6.4.3.6, 6.4.3.19, 6.4.4.6, 6.4.4.7,
  6.4.4.9, 6.4.4.10, 7.1.11 and 7.1.13
- Corrected combined-task titles in cis_1.1.2.1.x.yml - 1.1.2.1.3 is nosuid and 1.1.2.1.4 is
  noexec, and in cis_6.4.4.x.yml for 6.4.4.2 and 6.4.4.3
- Corrected copy-paste titles on the 2.1.6 mask task (was samba) and the 5.3.3.3.1 remember task
- Level tags aligned to Profile Applicability for 1.1.2.3.1, 1.1.2.4.1, 1.1.2.5.1, 1.7.8, 1.7.9,
  2.1.11, 2.1.20, 3.3.11, 4.3.3.1, 6.1.3 and 6.4.3.15
- Added deb11cis_rule_6_1_3 and deb11cis_apport_mask to the goss vars template so the audit can
  gate on them
- Corrected stale v1.0.0 control numbers in defaults/main.yml comments and the README tag example
- ansible_vars_goss.yml.j2 renamed lockdown_audit.yml.j2
- pre-commit update
- removed files not required
- audit variables and defaults now structured to override easily default/main/{filename}.yml

### QA pass

- Added the three handlers the role notifies but never defined: Update_Initramfs, Iptables
  persistent and Ip6tables persistent. Firewall rules were never persisted and initramfs was
  never rebuilt
- 2.1.21 notified Restart_postfix but the handler is named Restart postfix, so postfix was
  never restarted
- Dropped the notify to a handler named "update auditd" that has never existed
- post.yml only notified Reload sysctl; the Sysctl flush ipv4 and ipv6 route table handlers
  were unreachable, so route caches were never flushed after the sysctl templates changed
- 5.4.2.3 was tagged rule_5.4.2.2, so --tags rule_5.4.2.3 skipped the control entirely
- Migrated ansible_facts dot notation to bracket notation, 38 lines
- goss binary aligned to krameff v0.5.0 to match the other Debian and RHEL roles
- lockdown_audit.yml.j2 now starts with --- as the document start
- Corrected section comments naming controls that do not exist in v2.0.0 (6.2.3 rsyslog,
  6.2.2.1.2, 5.4.4, IPv5, pam_history) and assorted typos
- actions/checkout pinned to v7.0.0 to match the other roles

### Fixes

- prelim_interactive_users was declared as an empty list in vars/main.yml and never populated, so
  the two 7.2.9 ACL tasks looped over nothing and home directory default ACLs were never applied.
  prelim.yml now gathers username, uid and home and builds the list of dicts.
- 7.2.9 set ACLs on home directories but never removed excessive permissions from the directory
  itself, so /home/<user> stayed at 0755. Added the mode task the control asks for.
- 5.4.1.2 set password_expire_max when applying the minimum age to existing accounts. Enabling
  deb11cis_force_user_mindays would have set PASS_MAX_DAYS to the minimum value and expired every
  password. Now sets password_expire_min.
- The 3.1.2 wireless blacklist task was titled "3.2.1 | PATCH | Ensure dccp kernel module is not
  available", a copy-paste from section 3.2.

## Based on CIS V2.0.0 - Branch 2026_May_QA

- Update min_ansible_version to 2.16.1 (meta + vars)
- Fix LICENSE company name casing (MindPoint)
- Standardize changelog filename to CHANGELOG.md
- Remove export_badges_public.yml and update_galaxy.yml from private repo
- Add community.docker.docker to container detection
- Rewrite is_container.yml with correct Deb11 v2.0.0 rule IDs
- Add missing toggle deb11cis_rule_6_1_3 (benchmark rec 6.1.3)
- Add container guards to auditd handlers
- Add sshd -t validation to Restart sshd handler
- Fix handler notify mismatch (Set_reboot_required -> Change_requires_reboot)
- Add args: executable: /bin/bash to piped shell commands (Debian uses dash)
- Fix register order (register after changed_when/failed_when)
- Add no_log to shadow file tasks
- Add file_managed_by_ansible header to audit template
- Fix SELinux references to AppArmor
- Fix check_prereqs.yml: replace libselinux with python3-apt
- Add rule 6.1.3 task implementation (AIDE audit tool integrity)
- Fix typo in AIDE cron day variable (ddeb11cis -> deb11cis)
- Fix broken handler notify chains (dconf, systemd daemon reload)
- Convert sshd handler from block to listen pattern (Ansible 2.19 compatibility)
- Add ufw to molecule prepare packages
- Update meta author to Ansible-Lockdown Team
- Create molecule scenarios (default, localhost, wsl) with audit enabled

Apr 2026 - April 2026

- tidy up of legacy confusing default variables and defaults for 5.1
- pre-commit update

Mar 2026 - March26_alignment branch

- Common files alignment
  - `vars/main.yml`: `company_title` aligned
  - workflow updates
- Debian 11 benchmark validation run against private role (task names/tags, rule compare, audit content, spelling)
- Variable alignment across remediate and audit
- tidy up of variables not required


Feb 2026 QA Updates

  - QA grammar and audit template fixes
    - Fixed repeated words in defaults/main.yml: `of of` -> `of` (lines 695, 703, 1050)
    - Fixed subject-verb disagreement: `This variables is` -> `This variable is` (defaults/main.yml)
    - Fixed subject-verb disagreement: `values is` -> `value is` (defaults/main.yml)
    - Fixed typo: `5Allow` -> `Allow` (defaults/main.yml)
    - Fixed repeated words in task names: `is  is` -> `is` (5.1.9, 5.3.3.2.5)
    - Fixed repeated words in templates/ansible_vars_goss.yml.j2: `of of` -> `of`
    - Fixed audit template indentation for time_servers block consistency (templates/ansible_vars_goss.yml.j2)

Jan 2026

  - QA updates and linting fixes
    - Updated .ansible-lint config (removed deprecated parseable and verbosity options)
    - Updated .yamllint config (comments-indentation set to false for ansible-lint compatibility)
    - Fixed nginx service name typo in 2.1.18
    - Fixed spelling errors across multiple files
      - defaults/main.yml: `wont` -> `will not`, `thier` -> `their`
      - templates/ansible_vars_goss.yml.j2: `controling` -> `controlling`, `dependancy` -> `dependency`, `seperated` -> `separated`
      - templates/chrony.conf.j2: `usuable` -> `usable`
      - templates/ntp.conf.j2: `recquired` -> `required`, `synchonisation` -> `synchronisation`
      - templates/etc/sysctl.d/60-kernel_sysctl.conf.j2: `Adress` -> `Address`

Dec 2025

  - fw port and variables updated 4.1.5
  - 6.1.3 aide timer updates and improvements
  - typos fixed
  - logic for ansible 2.19

Oct 2025

  - changed to symbolic mode 6.2.1.1.3
  - README layout updates
  - workflow improvements
  - audit updates
    - max-concurrent process options added

June 2025 QA Updates

  - Update to audit_only to allow fetching results
  - resolved false warning for fetch audit
  - Improved documentation and variable compilation for crypto policies

May 2025 QA Fixes

  - Based on @polski-g fixes and improvements in DEB12
