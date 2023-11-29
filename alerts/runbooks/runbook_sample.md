# [RFC] CPU_high_usage_ENV_XXm

# Description

This alert indicates high CPU usage on a node for the last XX minutes.

## Alert confirmation

Check `CPU Busy` metrics on the `CPU Basic` graph of `Node Exporter Full` Grafana dashboard. The link to the Grafana dashboard can be found in the alert itself, check alert's annotations in Opsgenie.

The sum of `Busy *` metrics for the last XX minutes should be high(e.g. ≥ 80%). Ensure you're checking the right `Source` and time window.

## Criticality evaluation

<aside>
🚨 `CPU_high_usage_production_30m` is considered a critical issue and must be investigated ASAP.

</aside>

High CPU usage can affect all processes that run on a node. Examples:

- Performance degradation
- System unresponsiveness
- Termination of the application inside a container
- Node accessibility problems

## How to solve

1. Look at the `CPU` graph in the `CPU / Memory / Net / Disk` row of `Node Exporter Full` Grafana dashboard and check what is utilizing CPU the most (System/User/Iowait/etc)
2. Check the `Resource details` row on the `Applications Overview` Dashboard and identify a “problematic” process
3. Check app-specific runbooks to see if the problem is described there.
4. Check the problematic app’s metrics for anomalies and logs for errors.
5. Check if the problem started after any recent app update/redeploy.
6. Consider roll-backing the changes if the problem appeared after a recent update/redeploy.
7. Check whether these CPU usage spikes were present in the past. Is this behavior expected for this particular app?
8. Review system resources. Ensure your server has adequate resources (CPU, memory, disk, network, etc) for the workload.
9. If this amount of CPU usage expected you should consider resizing the host system to add more CPU cores.
10. Restart or redeploy the app (restarting an app will likely cause downtime). It may help in some cases, but there is no guarantee.

## Escalation

1. If you don’t know what to do, contact the team responsible for the machine/app that is causing issues. 
2. If this is your team, contact colleagues who are more familiar with a particular app causing issues.

If even the responsible team didn’t manage to solve the problem, ask @team-devops for help by making a thread in the `#devops` Discord channel describing all the details:

- When you received the alert
- What information was collected (the more details you provide, the better)
- What was done prior to the alert
- What was done after
- Steps to reproduce (if possible)

## Additional notes

If some alerts are firing regularly but don’t require any reaction, consider disabling them

## Useful links

- some link
