# pihole-unbound-rpi

Example setup of Pihole with Unbound for Raspberry Pi.

Using official Pihole Docker image and mvance/unbound-rpi for Unbound.

Clone this repo and a simple `docker compose up -d` should be enough.

Modify the `compose.yaml` to suit your setup.

Also modify `required/unbound/unbound.conf` to suit your setup.

The files `required/dnsmasq.d/09-pihole-local-subdomains.conf` and `required/dnsmasq.d/10-pihole-dhcp.conf`
are empty placeholders for when you want to customize Pihole with that.

The files `required/a-records.conf`, `required/forward-records.conf` and `required/srv-records.conf`
are empty placeholders for when you want to add those custom records to Unbound.
