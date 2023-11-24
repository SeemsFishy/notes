# CPU_high_usage_ENV_XXm

# Description

This alert indicates high CPU usage on a node for the last XX minutes.
Node exporters report these alerts from each node.

## Alert confirmation

Check `CPU Busy` metrics on the `CPU Basic` graph of `Node Exporter Full` Grafana dashboard. The link to the Grafana dashboard should be in the alert itself, check alert's annotations in OpsGenie.

The sum of `Busy *` metrics for the last XX minutes should be above 80%. Ensure you're checking the right `Source` and time window.

## Criticalness

The alert can affect all processes that run on a node. Issues that could be the result of high CPU usage:

- General slowdowns of all the software running on an affected node
- Node accessibility problems
- etc.

`CPU_high_usage_production_30m` is considered a critical issue and must be investigated ASAP.

## How to solve

- Look at the `Detailed CPU graph` and check what is utilizing CPU the most (System/User/Iowait/etc)
- Check Resource details row on `Applications Overview` Dashboard and identify a “problematic” process
- Check the problematic app’s metrics and logs
- Check recent activity, maybe the app was updated/redeployed?
- Review system resources. Ensure your server has adequate resources (CPU, memory, disk, network, etc) for the workload.
- Further steps could vary depending on the app causing the issues. Consult the corresponding app's runbooks

## Escalation

If you don’t know what to do, contact the team responsible for the machine/app that is causing issues. If this is your team, contact more experienced colleagues. If even the responsible team didn’t manage to solve the problem, ask @team-devops for help by making a thread in the `#devops` Discord channel describing all the details:

- When you received the alert
- What information was collected (the more details you provide, the better)
- What was done prior to the alert
- What was done after
- Steps to reproduce (if possible)

## Additional notes

If some alerts are firing regularly but don’t require any reaction, consider disabling them - [[RFC] Disabling alerts and setting `maintenance` windows](https://www.notion.so/RFC-Disabling-alerts-and-setting-maintenance-windows-10860ed03c624c00bd1bf88cd1bf73c2?pvs=21) 

## Useful links

- [Runbooks list](https://www.notion.so/c4b19865b32e43e9b801d8d83fc15fed?pvs=21)
- [Team Roster](https://www.notion.so/28692767a8534540bd38a2b688b17837?pvs=21)
- [Lido Applications](https://www.notion.so/bf710ed15c4f40c8b170d30ee4d8efe1?pvs=21)
- [[RFC] Alerts naming and rules configuration convention](https://www.notion.so/RFC-Alerts-naming-and-rules-configuration-convention-8b678ecba2714fbc92122f5956fe969e?pvs=21)
- [[RFC] Disabling alerts and setting `maintenance` windows](https://www.notion.so/RFC-Disabling-alerts-and-setting-maintenance-windows-10860ed03c624c00bd1bf88cd1bf73c2?pvs=21)

## TODO

- Discuss escalation