# Example of Pihole (v5) with Unbound for Raspberry Pi.

Using [official Pihole Docker image](https://hub.docker.com/r/pihole/pihole) and [mvance/unbound-rpi](https://github.com/MatthewVance/unbound-docker-rpi) for [Unbound](https://nlnetlabs.nl/projects/unbound/about/).

After cloning this repo, your structure should look like this:

```
   ├── compose.yaml
   └── required
    └── dnsmasq.d
        ├── 09-pihole-local-subdomains.conf
        ├── 10-pihole-dhcp.conf
    └── unbound
        ├── a-records.conf
        ├── forward-records.conf
        ├── srv-records.conf
        └── unbound.conf
```

* Modify the `compose.yaml` to suit your setup.

* If you are **not** using a Raspberry Pi, change `image: mvance/unbound-rpi:latest` into `image: mvance/unbound:latest`

* Modify `required/unbound/unbound.conf` to suit your setup.

* In Pihole WebUI, add Unbound as upstream DNS with IPv4 `127.0.0.1#5353` (note the #).

The files `required/dnsmasq.d/09-pihole-local-subdomains.conf` and `required/dnsmasq.d/10-pihole-dhcp.conf`
are empty placeholders for when you want to customize Pihole with that.

Example content of `09-pihole-local-subdomains.conf` to create custom local wildcard subdomains:

```
address=/.home.example.com/192.168.20.80
```

Example content for `10-pihole-dhcp.conf` to supply additinal options to Pihole´s DHCP server:

```
### give out two DNS (option 6) servers through DHCP
dhcp-option=6,192.168.20.50,192.168.20.51
### give out specific IP for NTP (option 42)
dhcp-option=42,192.168.20.40
### define tags for devices that will receive Google DNS instead through DHCP
dhcp-option=tag:googlednsv4,6,8.8.8.8,8.8.4.4
### assing above tag to a specific device by MAC
dhcp-host=AB:AB:AB:AB:AB:AB,set:googlednsv4
```

The files `required/unbound/a-records.conf`, `required/unbound/forward-records.conf`
and `required/unbound/srv-records.conf` are empty placeholders for when you want to add those custom records to Unbound.

**This is not a guide. This should only serve you as a example for your own setup.**

**Please refer to the documentation of Pihole, the unbound image and Unbound itself.**
