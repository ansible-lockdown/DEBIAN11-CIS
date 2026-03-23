# Debian11CIS

## Based on CIS V2.0.0

Mar 2026 — aligned from Private-DEBIAN11-CIS

- Common files aligned
- Removed public-only section 6.4.x task stubs and 6.4.x defaults toggles in favour of private 6.3.x numbering (matches audit JSON alias expectations)
- Debian 11 benchmark validation run against private role (task names/tags, rule compare, audit content, spelling)
- Variable alignment across remediate and audit
- tidy up of variables not required

Oct25
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
