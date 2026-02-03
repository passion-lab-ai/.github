# Security Policy

## Supported Versions
This project is currently **pre-release**. There are no public releases, and no versions are considered supported for production use.

## Reporting a Vulnerability
If you discover a security vulnerability, please report it privately by emailing **support@passionlabs.ai**.

Please include:
- A clear description of the issue and its potential impact
- Steps to reproduce (proof-of-concept if possible)
- Affected components, endpoints, or files
- Any relevant logs, screenshots, or traces
- Your contact information for follow-up

We ask that you **do not** disclose the issue publicly until we have investigated and published a fix or mitigation.

## Our Response Process
When we receive a vulnerability report, we aim to:
1. **Acknowledge receipt** within **3 business days**
2. **Triage and assess severity** (impact, exploitability, affected scope)
3. **Work on a fix or mitigation**
4. **Notify the reporter** when a fix is available or the issue is otherwise resolved

For high-severity issues, we may implement temporary mitigations while a full fix is prepared.

## Security Testing and Hardening (Pre-release)
Before release, we are implementing:
- Code review and CI security checks (e.g., SAST and dependency scanning)
- Secrets scanning and credential hygiene
- Least-privilege IAM and secure configuration reviews

## Scope
This policy applies to:
- Source code and build artifacts of this repository
- Staging/pre-release deployments operated by Passion Labs

Third-party services or dependencies are handled according to their respective security policies.

## Safe Harbor
We support good-faith security research. We will not pursue legal action against researchers who:
- Make a good-faith effort to avoid privacy violations, data destruction, and service disruption
- Only access data necessary to demonstrate the vulnerability
- Report the issue promptly to **support@passionlabs.ai**
