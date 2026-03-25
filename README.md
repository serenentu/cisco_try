# cisco_try

This repository contains Cisco Packet Tracer project files:

- `16th.pkt`
- `cisco.pkt` (empty/base file for custom build-out)

## Complete `16th.pkt`

Because `.pkt` is a binary Packet Tracer file, complete it by applying the CLI commands in:

- `configs/full_16th_completion.txt` (full end-to-end steps)
- `configs/config_block_0.txt` (Extended ACL 101)
- `configs/config_block_1.txt` (Extended ACL 102)
- `configs/interface_example.txt` (interface ACL attachment examples)
- `configs/show_working_configs_and_addresses.txt` (all show commands for working configs and addressing proof)

Open `16th.pkt` in Cisco Packet Tracer, apply the commands on the RS routers (Research Services side in the topology), then verify:

- `show access-lists`
- `show run | section access-list`
- `show ip interface <interface>`
- `show ip route`

## Topology completion goal (ping-based)

For this project, treat completion as: **topology is connected and devices can ping each other across required paths**.

Minimum verification in Packet Tracer:

- Confirm interfaces are up (`show ip interface brief` on routers)
- Ping across networks from one end device to another
- Confirm `0% loss` on allowed end-to-end paths

Primary checks to mark topology as completed:

- Ping between allowed networks succeeds
- Ping is blocked where ACL policy applies
- Routing tables are present and correct (`show ip route`)
- Cross-router connectivity is demonstrated end-to-end

To present **all working configs and addresses** for checking/demo, run the command pack in:

- `configs/show_working_configs_and_addresses.txt`

Example output snippet screenshot:

![Packet Tracer topology ping snippet](https://github.com/user-attachments/assets/45e5427b-7c9d-4417-911d-7315ee3342cb)

Before ACL testing, also confirm:

- Router interface IPs and inter-router links are correctly configured
- Routing protocol/routes are present (static routing or RIP as required)
- Switch VLANs and port assignments (if VLANs are used)
- Host IP configuration (IP/mask/gateway) matches the addressing plan

## Complete `cisco.pkt` (custom version)

Use this custom completion checklist/command template:

- `configs/full_cisco_completion.txt` (my custom end-to-end completion flow for the empty `cisco.pkt`)
- `configs/show_working_configs_and_addresses.txt` (demo/verification command pack)

Open `cisco.pkt`, apply the checklist in `configs/full_cisco_completion.txt`, and verify end-to-end connectivity with successful allowed-path pings and failed blocked-path checks.
