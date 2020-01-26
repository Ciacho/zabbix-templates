# PowerDNS Server template
#### Version: 1.0.2

#### Description:
PowerDNS Server service monitoring template. This template is using:
- Zabbix active agent items
- powerdns webserver api (over http://localhost:8081)
- This version is for Zabbix 4.4 

#### Macros used by template:
| Macro                    | Default value       | Description                                         |
| :----------------------- | :------------------ | :-------------------------------------------------- |
| {$SVC_PDNS_SERVER_IP}    | 127.0.0.1           | IP address of webserver                             |
| {$SVC_PDNS_SERVER_PORT}  | 8081                | TCP port                                            |

#### Items
- TCP and UDP queries - number of UDP/TCP queries received
- TCP and UDP answers - number of answers sent out over UDP/TCP
- query cache hits and miss - number of hits/misses on the query cache
- uptime - uptime of process in seconds
- version - version of server
- incoming notifications - NOTIFY packets received
- overload drops - Queries dropped because backends overloaded

#### Graphs
- SVC::pdns_server::memory
- SVC::pdns_server::answers
- SVC::pdns_server::queries
- SVC::pdns_server::query cache

<p align=center>
![Graph](https://ciacho.github.io/pdns_server_queries_small.png)
</p>

#### Triggers
- SVC::pdns_server process is DOWN
- SVC::pdns_server has just (re)started
- SVC::pdns_server version has changed


#### Notes:
- To use this template add pdns.conf configuration file:
```
# webserver	Start a webserver for monitoring (api=yes also enables the HTTP listener)
webserver=yes
# webserver-address	IP Address of webserver/API to listen on
webserver-address=127.0.0.1
# webserver-allow-from	Webserver/API access is only allowed from these subnets
webserver-allow-from=127.0.0.1,::1
# webserver-password	Password required for accessing the webserver
# DON'T SET PASSWORD
# webserver-password=
# webserver-port	Port of webserver/API to listen on
webserver-port=8081
# webserver-print-arguments	If the webserver should print arguments
# webserver-print-arguments=no
```

#### Changelog
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
- 1.0.1
  - initial Version
