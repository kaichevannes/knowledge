# Networking

For system A to reach system B on a local network they are connected with a switch and a physical or virtual interface we can list with `ip link`. To add an ip address on the same network we use `ip addr add <ip> dev <interface-name>`.

To reach systems C and D on a separate network we need a router. Gateways are doors to the outside work from a local network, we can see our systems gateway with the `route` command. To specify a gateway use `ip route add <system-ip> via <router-ip>`. Because we don't want to specify the gateway for every ip we connect to, we can specify a default router with `ip route add default via <router-ip>` — where `default` is equivalent to `0.0.0.0`.

To persist networking changes they need to be added to `/etc/network/interfaces` file.

## DNS

Domain names are translated to ip addresses based on the `/etc/hosts` file. Referencing hosts by name in this way is called name resolution. Eventually managing these files became too complex to manage and were moved to a DNS server. We point our host to a DNS server by specifying the DNS server under `/etc/resolv.conf`. If a hostname is not found under `/etc/hosts` then it is looked up from the DNS server (the lookup order is adjustable based on `/etc/nsswitch.conf`). This is useful because if a host name changes IP address, it now just needs to be changed in one place.

We can add a search entry to `/etc/resolv.conf` which will be added to a DNS resolution if it isn't matched, e.g. `search mycompany.com` will resolve `ping web` to `web.mycompany.com`. We can add more like `search mycompany.com prod.mycompany.com apps.mycompany.com` etc.

In a DNS server, A records are IPv4 to hostname, AAAA records are IPv6 to hostname, CNAME is hostname to hostname.

## IPTABLES

IPTABLES are used to specify input, forward, and output security rules for network requests. We have chains of rules that accept or drop packets based on the source or destination ip and ports. `iptables -l` lists rules. `iptables -A` appends to the end of chain, `iptables -I` inserts at the start of the chain. We specify the protocol `-p`, source ip `-s`, destination port `--dport` and what to do with the packet `-j`.
