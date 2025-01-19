![Ejemplo de imagen externa](https://assets.zabbix.com/dist/images/logo.fd87efa6da9bed3fd8c9.svg)

# Zabbix Template for Cohesity

This repository contains a template to monitor Cohesity nodes using SNMP in Zabbix version 6.0.

## Description

The `Cohesity` template includes monitoring items and discovery rules specifically designed to collect key information from Cohesity devices. These items use SNMP OIDs to retrieve data such as:

- **Part Number**
- **Serial Number**
- **Sensor information (automatic discovery)**

### Key Features

1. **Individual Items**:
   - `Part Number` (OID: `.1.3.6.1.4.1.10297.5.1.16.7`): Retrieves the part number.
   - `Serial Number` (OID: `.1.3.6.1.4.1.10297.5.1.16.2`): Retrieves the serial number. Includes a trigger that generates an alert if no SNMP data is received within 2 minutes.

2. **Discovery Rules**:
   - SNMP-based discovery for sensors.
   - Prototype items include:
     - Specific sensors (OID: `1.3.6.1.4.1.10297.2.1.5.{#SNMPINDEX}`).
   - Preprocessing rules to enhance the readability of sensor names (e.g., string replacements).

3. **HTTP Tests**:
   - Verifies the availability of the web service on the Cohesity node via the URL: `https://{HOST.NAME}`.

## Requirements

1. **Zabbix**:
   - Version 6.0 or later.
2. **Cohesity Device**:
   - Configured to respond to SNMP queries.
3. **Access Permissions**:
   - Credentials for SNMP and web service access.

## Installation

1. Download the template file from this repository.
2. Import the template into your Zabbix server:
   - Navigate to **Configuration > Templates**.
   - Click **Import** and select the file `Nodo_Cohesity_C5000`.
3. Link the `Cohesity` template to the corresponding host:
   - Navigate to **Configuration > Hosts**.
   - Edit the host and link the template.

## Usage

### Basic Monitoring

- The system will automatically collect data configured in the template, such as the part number and serial number.
- Sensor data will be discovered and added dynamically based on the configured rules.

### Alerts

- The `No SNMP Data` trigger will generate an alert if no serial number data is received within 2 minutes.

## Customization

- You can edit the items, discovery rules, and triggers to meet your specific needs.
- Modify preprocessing strings to adjust the naming of sensors.

## Contributions

Contributions are welcome. If you want to add features or improve this template, feel free to submit a pull request.

