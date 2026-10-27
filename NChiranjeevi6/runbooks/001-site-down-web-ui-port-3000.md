# 001 - Site down: device web UI not opening (port 3000)

**Severity:** High (site offline)  **Environment:** Armbian board, SQLite-based iVIS software  **Ticket type:** Site down

> Draft from my ticket notes. Replace `<service-name>` and add your screenshots under `runbooks/images/`.

## Symptom
Field engineer reports the site is down. The device answers ping, but its web page on port 3000 does not open.

## Initial checks
1. Ping the device: replies, so the network path and host are up.
2. Open `http://<device-ip>:3000`: fails, so the application layer is the problem.
3. SSH in with PuTTY and check the service state.

```bash
ssh <user>@<device-ip>
systemctl status <service-name>
ss -tlnp | grep 3000
```

## Root cause
Application configuration was missing or corrupt, so the service was not serving on port 3000.

## Fix
1. Restore the configuration from the known-good backup.
2. Restart the service.

```bash
cp <backup-path>/<config-file> <config-path>/<config-file>
sudo systemctl restart <service-name>
```

## Verification
- `ss -tlnp | grep 3000` shows the port listening
- Web page loads; site shows online in the portal

## Prevention / follow-up
- Confirm scheduled config backups exist for the device
- Note the pattern in the ticket for recurring-fault review

## Screenshots
Add images here.
