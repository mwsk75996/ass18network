# ass18network

## Formål
Dette repository indeholder materiale til assignment 18 (network).

## Struktur / indhold

## Part 1
Part 1 består af konfiguration til to vSRX-routere (R1 og R2) i form af Junos-konfigurationer.

### part1_vsrxR1.json
- Beskrivelse: Konfiguration for vSRX **R1** (host-name: `R1`).
- Interfaces / net:
  - `ge-0/0/1.0` → `192.168.1.1/24` (Net1)
  - `ge-0/0/2.0` → `192.168.2.1/24` (Net2)
- Services:
  - SSH aktiveret
  - DHCP lokal server via `dhcp-local-server` (grupper **Net1** og **Net2**)
  - DHCP pools:
    - Net1: `192.168.1.10–192.168.1.100`, router `192.168.1.1`, DNS `8.8.8.8`
    - Net2: `192.168.2.10–192.168.2.100`, router `192.168.2.1`, DNS `8.8.8.8`
- Security:
  - `trust → trust` policy `default-permit`
  - Host-inbound tillader `ping`, `ssh` og `dhcp` på `ge-0/0/1.0` og `ge-0/0/2.0`

### part1_vsrxR2.json
- Beskrivelse: Konfiguration for vSRX **R2** (host-name: `R2`).
- Interfaces / net:
  - `ge-0/0/1.0` → `192.168.3.1/24` (Net3)
  - `ge-0/0/2.0` → `192.168.4.1/24` (Net4)
  - `ge-0/0/3.0` → `10.10.10.11/24` (transit/link mod R1)
- Services:
  - SSH aktiveret
  - DHCP server via `system services dhcp` (pools for Net3 og Net4)
  - DHCP pools:
    - Net3: `192.168.3.10–192.168.3.100`, router `192.168.3.1`, DNS `8.8.8.8`
    - Net4: `192.168.4.10–192.168.4.100`, router `192.168.4.1`, DNS `8.8.8.8`
- Routing:
  - Statiske routes til Net1 (`192.168.1.0/24`) og Net2 (`192.168.2.0/24`) via next-hop `10.10.10.10`
- Security:
  - `trust → trust` policy `default-permit`
  - Host-inbound tillader `ping`, `ssh` og `dhcp` på LAN-interfaces, og `ping`/`ssh` på transit-interface

## Part 2 (kommer)
Der kommer også en Part 2, som består af følgende dele:

### part2_vsrxR1
- Beskrivelse: (kommer)
- Konfiguration: (kommer)
- Noter / tests: (kommer)

### part2_vsrxR2
- Beskrivelse: (kommer)
- Konfiguration: (kommer)
- Noter / tests: (kommer)