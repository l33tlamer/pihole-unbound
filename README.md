# pihole-unbound-rpi

Example setup of Pihole with Unbound for Raspberry Pi.

Using official Pihole Docker image and mvance/unbound-rpi for Unbound.

After cloning this repo, your structure should look like this:

```
   ├── compose.yaml
   └── required
    └── dnsmasq.d
        ├── 09-pihole-local-subdomains.conf
        ├── 10-pihole-dhcp.conf
    └── etc-pihole
    └── unbound
        ├── a-records.conf
        ├── forward-records.conf
        ├── srv-records.conf
        └── unbound.conf
```

Modify the `compose.yaml` to suit your setup.

Also modify `required/unbound/unbound.conf` to suit your setup.

A simple `docker compose up -d` should be enough.

Login to the Pihole WebUI at `http://<host-ip>/admin` and change your settings.

Add Unbound as upstream DNS with IPv4 `127.0.0.1#5353` (note the #).

The files `required/dnsmasq.d/09-pihole-local-subdomains.conf` and `required/dnsmasq.d/10-pihole-dhcp.conf`
are empty placeholders for when you want to customize Pihole with that.

The files `required/unbound/a-records.conf`, `required/unbound/forward-records.conf`
and `required/unbound/srv-records.conf` are empty placeholders for when you want to add those custom records to Unbound.
