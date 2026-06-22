# Omada Switch CLI Skill

## Project Goal

This is an Omada Switch CLI Skill for TP-Link Omada managed switches.

The Skill focuses on two workflows:

1. Explain how a supported TP-Link Omada switch feature is configured from the official CLI command model.
2. Generate concrete CLI configuration suggestions from a natural-language requirement and explain each command line.

This version prioritizes accuracy: it only generates commands traceable to official CLI documentation in the knowledge base.

## Supported Scope

This version supports these capabilities:

- Basic interface configuration: interface selection, interface ranges, port descriptions, enable/disable, speed, duplex, flow control, and interface status/configuration display.
- Etherchannel / LAG / LACP: static LAG, LACP active/passive, aggregation load balancing, LACP priority and timeout, and aggregation status display.
- IEEE 802.1Q VLAN: VLAN creation, deletion, naming, display, port VLAN membership, tagged/untagged handling, PVID, VLAN Trunk, and Ingress Checking.
- System configuration: system time, system identity, management VLAN, Layer 3 interface IP addressing, controller adoption helpers, reset/reboot, configuration save/backup/restore, TFTP/FTP/SCP/SFTP helpers, logging export, boot/image/firmware/patch/checkpoint/autoinstall, ping/tracert, system display, cable diagnostics, and power commands.
- CLI basics and user interface: CLI access-method notes, command modes, privilege-level notes, syntax conventions, line console entry, console media selection, enable/configure/exit/end, paging, command history, and privileged-mode password commands.
- User management: local user creation/removal, privilege levels, password/secret handling, password recovery, password-complexity policy, password cycle, and user/client display.
- File system: local file copy, path navigation, directory display, rename/delete, FTP view, FTP open/put/get/close.
- Dedicated management port: IPv4 DHCP/static configuration, IPv6 enable/address configuration, and display.
- EEE: EEE display and documented enable/disable syntax uncertainty.
- SDM templates: SDM template selection and SDM resource allocation display.
- Time ranges: time-range objects, absolute/periodic ranges, holiday behavior, holiday definitions, and display.
- Layer 2 switching and redundancy: port isolation, loopback detection, MLAG, MAC address table, MAC-based VLAN, protocol-based VLAN, private VLAN, VLAN-VPN, ERPS, GVRP, MSTP/STP, LLDP, L2PT, PPPoE ID-Insertion, and port mirroring.
- Multicast and multicast VLAN: IGMP Snooping, Layer 3 IGMP, PIM, PIM6, static multicast routing, MLD Snooping, IPv6 MLD, and MVR.
- Physical/OAM and operations: PTP, Stack, DDM, Debug, Dying Gasp, Ethernet OAM, DLDP, PoE, and System Log.
- Management access and protocols: HTTP/HTTPS, SSH, Telnet, Serial Port, sFlow, SNMP, and NETCONF.
- Layer 3 routing, overlay, and gateway redundancy: VRF, static routes, RIP/RIPng, OSPF/OSPFv3, BFD, BGP, L2VPN, IS-IS, URPF, Tunnel, IPv6 address, ARP, VRRP, MPLS, and LDP.
- DHCP, address allocation, and source/neighbor protection: DHCP Server/Relay, DHCPv6 Relay, DHCP L2 Relay, DHCPv6 L2 Relay, IPv4/IPv6 IMPB, IP/IPv6 Verify Source, DHCPv4/DHCPv6 Filter, ARP Inspection, and ND Detection.
- QoS and voice traffic: QoS, bandwidth control, OUI-Based VLAN, Voice VLAN, and Auto VoIP.
- Security, authentication, and access control: CPP, Access Control, AAA, IEEE 802.1X, Port Security, MACsec, ACL, and DoS Defend.

## Unsupported Scope

This version covers the task-book chapters through Chapter 95. If a user asks for behavior, platform support, or command syntax that is not present in `knowledge/`, the Skill should explain that the current knowledge base is insufficient and should not invent commands.

High-risk supported operations such as reset, reboot, firmware upgrade, boot/image changes, patch operations, checkpoint rollback, configuration restore, file delete, `clear config interface`, SDM template changes, management access changes, routing protocol changes, DHCP service/relay changes, source-guard/inspection filters, QoS/voice policy changes, authentication changes, ACL binding, PoE power control, SNMP/NETCONF exposure, OAM/MPLS/LDP/DLDP, and system logging exports should only be generated when explicitly requested, with a short risk note.

## File Structure

```text
omada-switch-cli-skill/
├── SKILL.md
├── README.md
├── pdf_uncertainties.md
└── knowledge/
    ├── 01_interface_configuration.md
    ├── 02_etherchannel.md
    ├── 03_ieee_802_1q_vlan.md
    ├── 04_system_configuration.md
    ├── 05_using_the_cli.md
    ├── 06_line_commands.md
    ├── 07_user_interface.md
    ├── 08_user_management.md
    ├── 09_file_system_configuration.md
    ├── 10_management_port_configuration.md
    ├── 11_eee_configuration.md
    ├── 12_sdm_template.md
    ├── 13_time_range.md
    ├── 14_port_isolation.md
    ├── 15_loopback_detection.md
    ├── 16_mlag.md
    ├── 17_mac_address.md
    ├── 18_mac_based_vlan.md
    ├── 19_protocol_based_vlan.md
    ├── 20_private_vlan.md
    ├── 21_vlan_vpn.md
    ├── 22_erps.md
    ├── 23_gvrp.md
    ├── 24_mstp.md
    ├── 25_lldp.md
    ├── 26_l2pt.md
    ├── 27_pppoe_id_insertion.md
    ├── 28_port_mirroring.md
    ├── 29_igmp_snooping.md
    ├── 30_layer3_igmp.md
    ├── 31_pim.md
    ├── 32_pim6.md
    ├── 33_static_multicast_routing.md
    ├── 34_mld_snooping.md
    ├── 35_ipv6_mld.md
    ├── 36_mvr.md
    ├── ...
    └── 95_system_log.md
```

The later testing stage adds:

```text
tests/
├── test_cases.md
└── test_report.md
```

## Usage

Ask how a supported feature is configured, for example:

```text
How do I configure an access-like port on an Omada switch?
```

Or enter a concrete natural-language configuration requirement, for example:

```text
Create VLAN 10 and name it Finance.
```

Or:

```text
Configure port 1/0/3 as a regular access-like port for VLAN 20.
```

Or:

```text
How do I enter configuration mode and disable CLI paging?
```

Or:

```text
Create an admin user named opsadmin with an unencrypted password.
```

Or:

```text
Configure the dedicated management port with IPv4 address 192.168.10.1/24.
```

Or:

```text
Create a time range named WorkHours from 08:30 to 18:00 on working days.
```

Or:

```text
Show the current SDM template resource allocation.
```

Or:

```text
Enable loopback detection on gigabitEthernet 1/0/5 and block the port when a loop is detected.
```

Or:

```text
Show LLDP neighbor information for gigabitEthernet 1/0/1.
```

Or:

```text
Create monitor session 1 with gigabitEthernet 1/0/1 as the destination and mirror ingress traffic from gigabitEthernet 1/0/4.
```

Or:

```text
Enable IGMP Snooping for VLAN 10 and show the learned multicast groups.
```

Or:

```text
Show IPv6 MLD Snooping groups for VLAN 20.
```

The Skill generates CLI suggestions based on the curated official-document content in `knowledge/`.

For colloquial access / trunk requests, the Skill does not generate other-vendor-style `switchport mode access` or `switchport mode trunk`. It maps the requirement to the IEEE 802.1Q VLAN configuration approach in the Omada official documentation, using commands such as `switchport general allowed vlan`, `switchport pvid`, and `vlan_trunk`.

Multi-switch deployment exports and full validation checklists are intentionally not first-stage workflows. They can be added later after the single-feature explanation and direct CLI-generation behavior is stable.

## Output Format

For direct CLI generation, Skill responses include these sections:

```markdown
### 1. Understood Requirement

### 2. CLI Configuration Commands

### 3. Line-by-Line Command Explanation

### 4. Overall Explanation

### 5. Disclaimer
```

For how-to explanation, Skill responses use a shorter structure:

```markdown
### 1. Configuration Idea

### 2. Key Commands or Template

### 3. Important Notes

### 4. Disclaimer
```

## Accuracy Principles

- Use only commands curated in `knowledge/`.
- Do not mix in CLI syntax from Cisco, H3C, Huawei, Aruba, Ruijie, or other vendors.
- Do not generate commands that do not appear in the official documentation.
- For uncertain PDF content, refer to `pdf_uncertainties.md` and avoid using uncertain examples as default recommended commands.
- If the knowledge base does not provide enough evidence, clearly state that the current version is unsupported or lacks sufficient information.

## Disclaimer

These CLI configurations are for reference only. Refer to TP-Link Omada official documentation, device model, firmware version, and the actual network environment, and back up the configuration before execution.
