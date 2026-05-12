# Changes to DEB11CIS

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

Mar 2026 — March26_alignment branch

- Common files alignment
  - `vars/main.yml`: `company_title` aligned
  - workflow udpates
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
