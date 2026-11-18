# Log Sources and Telemetry
---
**Telemetry** is the collection of events, metrics, alerts, and records that describe what happened in an environment.

## Time and Integrity
**Time Synchronization** is critical. If endpoint clocks drift five minutes behind accurate firewall clocks, an analyst may invert cause and effect. Use **Network Time Protocol (NTP)** against an authoritative source and store timestamps in **Coordinated Universal Time (UTC)** so events from different zones line up without conversion errors.

Logs must also be protected, because attackers routinely clear event logs, stop agents, or disable audit sttings to cover tracks.
