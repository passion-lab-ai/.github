# Security Integration Testing

All publicly accessible applications undergo automated security testing as part of PassionLab's vulnerability management program, supporting compliance with SOC 2 (CC6.1, CC7.1) and ISO 27001 (A.12.6).

The program covers three testing disciplines:

| Discipline | Description | Tool |
|---|---|---|
| **DAST** *(Dynamic Application Security Testing)* | Runtime testing of deployed applications to identify exploitable vulnerabilities | OWASP ZAP |
| **SAST** *(Static Application Security Testing)* | Analysis of source code and build artifacts for security defects prior to deployment | CodeQL |
| **SCA** *(Software Composition Analysis)* | Continuous monitoring of third-party dependencies for known CVEs and license risk | Dependabot |

## DAST Usage

Add the following job to the end of your deployment workflow. The target must be a publicly reachable URL — DAST is not applicable to environments behind a VPN or private network.

```yaml
dast:
    name: DAST (OWASP ZAP)
    needs: deploy
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: ZAP Baseline Scan
        uses: zaproxy/action-baseline@v0.14.0
        with:
          target: https://your-project.com
          token: ${{ secrets.GITHUB_TOKEN }}
```

Scan results are reported as GitHub Issues and surfaced in the Security tab. Critical and high findings must be remediated before promotion to production.

## Callable Workflow [Not yet implemented]

```yaml
dast:
  needs: deploy
  uses: passion-lab-ai/.github/.github/workflows/dast-scan.yml@main
  with:
    target_url: https://your-project.com
```



## SAST and SCA

CodeQL (SAST) and Dependabot (SCA) are configured organisation-wide and run automatically against all repositories. No per-repo configuration is required.

- **CodeQL** runs on every pull request and on a weekly schedule, scanning for security vulnerabilities and code quality issues in supported languages.
- **Dependabot** continuously monitors dependency manifests for known CVEs and raises pull requests to apply remediation. Security alerts are also surfaced in the Security tab of each repository.

**GitHub Secret Scanning** is also enabled organisation-wide. It detects secrets, tokens, and credentials committed to any repository and raises alerts immediately. Push protection is enforced to block commits containing recognised secret patterns before they reach the repository.

Findings from all tools follow the same remediation policy: critical and high severity issues must be resolved before merging to the default branch.


