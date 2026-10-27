# 002 - Site down: database service stopped

**Severity:** High (site offline)  **Environment:** Raspberry Pi OS, MySQL/MariaDB-based iVIS software (older version than 001)  **Ticket type:** Site down

> Draft from my ticket notes. Replace `<service-name>` and add your screenshots under `runbooks/images/`.

## Symptom
Site reported down by the field engineer; the device is reachable but the application is not working.

## Initial checks
```bash
ssh <user>@<device-ip>
systemctl status mariadb
htop
```
The MariaDB service was not running.

## Root cause
Database service stopped, so the application could not start properly.

## Fix
```bash
sudo systemctl start mariadb
sudo systemctl restart <service-name>
```
Then check the bundles in the local OSGi console (port 6666) and confirm all are active.

## Verification
- `systemctl status mariadb` shows active (running)
- OSGi console shows bundles active
- `htop` shows normal CPU/memory; site shows online in the portal

## Prevention / follow-up
- Check why the DB stopped (`journalctl -u mariadb`) and whether it should auto-start on boot (`systemctl enable mariadb`)

## Screenshots
Add images here.
