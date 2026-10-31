# 01 — OPNsense Installation and Initial Configuration

## Objective

The objective of this project was to replace my ISP-provided TP-Link EX520v router with a dedicated OPNsense firewall running on a mini-PC.

I wanted greater control over my home network and the opportunity to gain practical experience with firewall administration, routing, network interfaces, and troubleshooting.

## Hardware and Software

| Component | Purpose |
|---|---|
| Mini-PC | Dedicated firewall hardware |
| OPNsense 25.7 | Firewall and routing operating system |
| Fibrecast ONT | Connection to the ISP's fibre network |
| Netgear Ethernet switch | Connecting wired LAN devices |
| TP-Link EX520v | Repurposed as a wireless access point |
| Laptop | Firewall administration and network testing |

## 1. Initial Deployment

I deployed OPNsense on a dedicated mini-PC to act as the primary router and firewall for my home network.

The mini-PC was connected directly to the Fibrecast ONT through its WAN Ethernet interface.

A separate Ethernet interface was assigned to the internal LAN, allowing devices to communicate through OPNsense.

## 2. Interface Assignment

The following interfaces were configured:

| Interface | Assignment | Purpose |
|---|---|---|
| `igc0` | Physical WAN | Connection to the ISP ONT |
| `igc0_vlan911` | WAN VLAN | ISP-required VLAN tagging |
| `igc1` | LAN | Internal network connectivity |

The LAN interface was configured with the static IPv4 address `192.168.1.1/24`.

This address also serves as the default gateway for devices on the internal network.

## 3. Accessing the Management Interface

After configuring the LAN interface, I accessed the OPNsense web administration interface from a laptop connected to the internal network.

Management address:

`http://192.168.1.1`

The web interface provided access to network interface configuration, DHCP services, routing information, firewall settings, and system diagnostics.

## 4. Initial Connectivity Testing

Following the initial configuration, I performed connectivity tests to verify that the firewall was operating correctly.

These included:

- Checking the physical WAN and LAN interface status.
- Verifying the LAN IP address and subnet.
- Confirming that the WAN interface obtained an IPv4 address through DHCP after the required VLAN configuration.
- Testing connectivity to the ISP gateway.
- Testing external connectivity using `ping` and `traceroute`.
- Confirming internet access from a laptop connected to the LAN.

## 5. Outcome

OPNsense was successfully deployed as the main router and firewall for my home network.

The completed configuration provided a foundation for implementing DHCP, network switching, wireless access, and future security features such as VLAN segmentation and intrusion detection.

## Next Steps

The next stage involved configuring the ISP-required IEEE 802.1Q VLAN 911 and troubleshooting an unexpected LAGG interface configuration.

See [WAN and VLAN Configuration](02-WAN-VLAN-Configuration.md) once that document is available.
