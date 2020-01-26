# Zabbix templates

[![License: CC BY-SA](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/)

This repository provides a set of templates which offers the alternative set of templates to supplied by Zabbix.


## Changelog
### (devel)
See ![devel tree](https://github.com/Ciacho/zabbix-templates/tree/devel)
### 1.0.3
- **PowerDNS Server**
  - 1.0.3
    - Creating a template in a dedicated version for Zabbix 4.4
    - Creating a template in a dedicated version for Zabbix 4.0, 4.2
    - Changing regular expression for all items.
### 1.0.2
- **PowerDNS Server**
  - 1.0.2
    - Triggers:
      - SVC::pdns_server has just (re)started
      - SVC::pdns_server version has changed  
    - Items:
      - incoming-notifications
      - overload-drops
      - query-cache-hit
      - query-cache-miss
      - real-memory-usage
      - uptime
      - version
    - Graphs:
      - SVC::pdns_server::query cache
### 1.0.1
- **PowerDNS Server**
  - initial Version


## List of templates:
- [PowerDNS Server](https://github.com/Ciacho/zabbix-templates/tree/master/Service%20PowerDNS%20Server)


## Notes
- The naming pattern (application, items and triggers) is based on [Kloczek templates](https://github.com/kloczek/zabbix-templates)
* Each template has own version tag which is the copy of the whole zabbix-templates package version tag in which last changes has released
* Each template in the description field has the last modification date and internal version
* If it is something which needs to be done to use those templates it is described in each template within description notes
* Naming convention for the items names, applications and triggers must adhere naming convention using 2-4 letter abbreviations:
  ```
  <CLASS>::<Name>
  <CLASS>::<SUBCLASS>::<Name>
  ```
  ##### Items Examples:
  ```
  HW::CPU
  MEM::Total Memory
  NET::ICMP::Loss
  NTP::WTS::Clock Frequency Adjustment
  ```
  Above provide a parseable name, allowing us to distinguish between and categorise those objects.
  Such convention allows to handle use the pattern in alarming layer allowing on define actions. For example, send all trigger with SYS:: in the beginning name of the template to exact team.
  Such pattern is possible to use as part of the general interface on communication with external services.
* Do not use {HOSTNAME} macros in triggers. In web frontend from Monitoring -> Triggers table has "host" column with the host name of the the active trigger. Repeating second time this hos name in the trigger name it is waste of space on the web page.
* All zabbix agent items should be specified as ```zabbix agent (active)``` items.
* All graphs resolution needs to be 1200x300.

##### Copyright (C) 2017-2020 Tomasz T. Ciaszczyk <tomasz@ciaszczyk.art.pl>

##### This program is free software, distributed under the terms of the CC BY-SA.
