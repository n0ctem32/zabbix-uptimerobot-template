# Zabbix Template for UptimeRobot Monitoring

This Zabbix template allows you to monitor [UptimeRobot](https://uptimerobot.com/) Monitors and Status Pages via their API.

## Features

- Uses **HTTP agent** to pull data from UptimeRobot API.
- Supports **low-level discovery (LLD)** for:
  - Monitors
  - Public Status Pages (PSPs)
- Gathers and visualizes:
  - Uptime ratios (1d, 7d, 30d)
  - Downtime durations
  - Monitor logs
  - Response times
  - Monitor status, type, URL, and name
- Contains **trigger prototypes** for alerting:
  - Down or paused monitors
  - Inactive status pages
- Includes **value maps** for human-readable status/type names.

## Requirements

- Zabbix 7.2 or later
- UptimeRobot (with API access)
- HTTP Agent enabled in Zabbix server

## Setup Instructions

1. **Import the template:**
   - Go to **Configuration → Templates**
   - Click **Import**
   - Upload the YAML template file (`zabbix-uptimerobot-template.yaml`)
   - Ensure all checkboxes are selected and click **Import**

2. **Create a new Host and setup the macro:**
   Go to **Host → Macros**, and add:

   ```
   {$UPTIMEROBOT_API_KEY} = 'YOUR_API_KEY'
   ```

## Notes

- `uptimerobot.discovery.monitors` fetches monitor data.
- `uptimerobot.discovery.psp` fetches public status page data.
- Values like uptime ratio and downtime durations are parsed using `JSONPath` and post-processed using `JavaScript` steps.
- Triggers are prototype-based and will dynamically generate alerts per discovered monitor/PSP.

## Value Maps

Included:

- **UptimeRobot Status**
- **UptimeRobot Type**
- **UptimeRobot Status Page Status**

## Work in Progress

- **Logs for the individual monitors are still being worked on.**
- **If you have suggestions, please leave them in an issue or a pull request.**

## License

MIT License

---

**Author:** [n0ctem32](https://github.com/n0ctem32)  
Contributions and improvements welcome!
