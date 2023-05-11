# bypass ping mikrotik


```
/ip firewall mangle
add action=mark-packet chain=forward new-packet-mark=icmp_pkts passthrough=no protocol=icmp comment="Bypass Ping"
add action=mark-packet chain=input new-packet-mark=icmp_pkts passthrough=no protocol=icmp comment="Bypass Ping"
add action=mark-packet chain=prerouting new-packet-mark=icmp_pkts passthrough=no protocol=icmp comment="Bypass Ping"
add action=mark-packet chain=postrouting new-packet-mark=icmp_pkts passthrough=no protocol=icmp comment="Bypass Ping"
add action=mark-packet chain=output new-packet-mark=icmp_pkts passthrough=no protocol=icmp comment="Bypass Ping"
```
Pindah ke paling atas di manglenya



```
/queue simple
add max-limit=5M/5M name=ICMP_Priority packet-marks=icmp_pkts target=""
```
Pindahkan ke paling atas di Simple Queues nya
