# Security Policy

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| Latest on `main` | :white_check_mark: |

This project is a single-script tool (`sccmpatch.ps1`) without semantic versioning releases.
Only the current version on the `main` branch receives updates.

## Reporting a Vulnerability

If you discover a security vulnerability in this project, please report it responsibly:

1. **Do not** open a public GitHub issue for security vulnerabilities.
2. Email the maintainer at the address listed in the repository profile, or use [GitHub's private vulnerability reporting](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability) for this repository.
3. Include a description of the vulnerability, steps to reproduce, and potential impact.
4. You can expect an initial response within 7 business days.

## Security Considerations

This script operates with elevated privileges and interacts with infrastructure components:

- **WinRM**: The script uses `Invoke-Command` over WinRM. Ensure WinRM is configured with HTTPS (port 5986) or Kerberos authentication rather than basic/plaintext HTTP.
- **Service account**: The Veeam Backup Administrator account used to run this script should follow least-privilege principles and must not have MFA enabled (Veeam PowerShell limitation per KB4535).
- **Execution policy**: The script requires an execution policy that permits script execution. Use `RemoteSigned` or `AllSigned` rather than `Unrestricted`.
