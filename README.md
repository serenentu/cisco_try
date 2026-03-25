# cisco_try

This repository contains the Cisco Packet Tracer project file `16th.pkt`.

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

To present **all working configs and addresses** for checking/demo, run the command pack in:

- `configs/show_working_configs_and_addresses.txt`

Before ACL testing, also confirm:

- Router interface IPs and inter-router links are correctly configured
- Routing protocol/routes are present (static routing or RIP as required)
- Switch VLANs and port assignments (if VLANs are used)
- Host IP configuration (IP/mask/gateway) matches the addressing plan
