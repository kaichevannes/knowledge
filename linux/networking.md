# Networking

## DNS

Domain names are translated to ip addresses based on the `/etc/hosts` file. Referencing hosts by name in this way is called name resolution. Eventually managing these files became too complex to manage and were moved to a DNS server. We point our host to a DNS server by specifying the DNS server under `/etc/resolv.conf`. If a hostname is not found under `/etc/hosts` then it is looked up from the DNS server (the lookup order is adjustable based on `/etc/nsswitch.conf`). This is useful because if a host name changes IP address, it now just needs to be changed in one place.

We can add a search entry to `/etc/resolv.conf` which will be added to a DNS resolution if it isn't matched, e.g. `search mycompany.com` will resolve `ping web` to `web.mycompany.com`. We can add more like `search mycompany.com prod.mycompany.com apps.mycompany.com` etc.

In a DNS server, A records are IPv4 to hostname, AAAA records are IPv6 to hostname, CNAME is hostname to hostname.
