# FounderOS Safety / Recovery Integration

This document links Hermes Desktop to the FounderOS safety and recovery control plane.

Canonical implementation:
- FounderOS repository: lucadeg/MVX_Hermes_FounderOS
- FounderOS draft PR: #84
- Canonical runbook: docs/operations/HERMES_DESKTOP_SAFETY_RECOVERY_TRIPLE_BACKUP_RUNBOOK.md
- Project Council: FounderOS private issue #85

Integration expectations for Hermes Desktop:

1. Surface FounderOS safety state and forensic-ledger health.
2. Surface Desktop Commander online/offline/watchdog state.
3. Surface last successful local backup, Drive replication and restore drill.
4. Preserve FounderOS correlation IDs in Desktop agent actions.
5. Refuse destructive automation when the FounderOS safety gate or ledger is unavailable.
6. Link users to the canonical recovery runbook during incidents.
7. Never embed backup OAuth tokens, rclone credentials, API keys or raw Antigravity secrets.
8. Treat D: as the offline emergency toolkit and E: as the local recovery target.

Current acceptance gate:

FounderOS PR #84 must remain draft until target-machine validation passes, including:
- focused safety tests;
- PowerShell parsing;
- Woodpecker exact-head gate;
- offline D: model startup;
- E: capacity preflight and repository backup;
- one full restore drill;
- Google Drive additive replication;
- ledger verification;
- Desktop Commander reconnect/watchdog test.

No Hermes Desktop code or release behavior should assume these controls are active until the above evidence exists.