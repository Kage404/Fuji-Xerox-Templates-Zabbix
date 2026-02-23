Zabbix Template: Printer SNMP Fuji Xerox by Rizqi






A comprehensive Zabbix template for monitoring Enterprise Printers (especially Fuji Xerox) using the SNMP protocol. This template includes Low-Level Discovery (LLD) to automatically detect all printer consumable components (Toner, Drum, Waste Cartridge) without manual configuration for each item.

🌟 Key Features

Availability Monitoring: Monitor printer up/down status using ICMP Ping.

Total Page Counter: Monitor the total number of printed pages.

Low-Level Discovery (LLD): Automatically detects printer supplies:

Black/Cyan/Magenta/Yellow Toner Cartridge

Black/Cyan/Magenta/Yellow Drum Cartridge

Waste Toner Cartridge

Supply Metrics:

Maximum Capacity

Current Capacity

Remaining Percentage (Calculated %)

Smart Triggers (Alerts):

🔴 Disaster: Printer Offline (3 consecutive ping timeouts)

🟡 Warning: Consumable below 10%

🟠 High: Consumable below 5% (Critical)

🔴 High: Consumable completely empty (0%)

Automated Graphs: Automatic graphs for supply percentage levels, Current vs Max ratio, and Total Page Counter trends.

📋 Requirements

Zabbix Server version 6.4 or later.

Fuji Xerox printer (or other enterprise printers that support RFC 3805 MIB).

SNMP protocol (v1/v2c/v3) enabled in the printer’s network settings.

🚀 Installation Guide

Download the file PrinterFujiXerox_SNMP_Supplies_Zabbix6.xml from this repository.

Log in to your Zabbix dashboard.

Navigate to Data collection → Templates.

Click the Import button in the top-right corner.

Select the downloaded XML file, check Update existing and Delete missing, then click Import.

Navigate to Data collection → Hosts and add your printer host.

On the host configuration:

Add Interfaces: SNMP (enter the printer IP address) and configure the SNMP version/community according to your printer settings (e.g., public).

Link the template Printer SNMP Fuji Xerox by Rizqi to the host.

Wait a few minutes for Zabbix to start polling data.

💡 Troubleshooting

Q: Why do I get the error Cannot evaluate function: item does not exist in the Calculated Item (Percentage) after import?
A: This is normal. The Percentage item uses a mathematical formula based on Current and Max values. If Zabbix has not performed the first SNMP polling yet, the formula will temporarily fail.

Solution:
Wait approximately 5 minutes, or force data collection by navigating to:
Hosts → Select your Printer Host → Items tab → Check the SNMP supply items → Click Execute now.

The error will automatically disappear once data is received.

🤝 Contributing

Pull requests are welcome! If you find a bug or would like to add new features (for example, Paper Tray Status monitoring), feel free to open an issue or submit a PR.
