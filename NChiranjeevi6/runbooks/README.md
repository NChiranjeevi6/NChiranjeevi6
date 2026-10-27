# Field Runbooks

Sanitized write-ups of real support tickets. Format: **Symptom -> Checks -> Fix -> Verify -> Prevent**.

| # | Runbook |
|---|---|
| 001 | [Site down: device web UI not opening (port 3000)](001-site-down-web-ui-port-3000.md) |
| 002 | [Site down: database service stopped](002-site-down-mariadb-service.md) |

New runbook? Copy [TEMPLATE.md](TEMPLATE.md).

## Sanitization checklist (do this before every commit)
- [ ] No customer, bank or branch names
- [ ] No real IP addresses, hostnames, serials or site IDs (use `<device-ip>`, `<site-id>`)
- [ ] No passwords, tokens, TOTP seeds or config files with secrets
- [ ] Screenshots cropped or blurred; check browser tabs and terminal titles
- [ ] Nothing your employer has marked confidential
