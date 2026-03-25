# Cisco commands to complete `16th.pkt`

`16th.pkt` is a Packet Tracer binary file and cannot be directly edited with the CLI tools in this environment.

Use the files in this folder to complete device configuration in Packet Tracer manually:

- `full_16th_completion.txt` → Full end-to-end completion checklist/commands for `16th.pkt`
- `config_block_0.txt` → Extended ACL 101
- `config_block_1.txt` → Extended ACL 102
- `interface_example.txt` → Interface ACL attachment example
- `rs_subnets.txt` → RS subnet allocation reference
- `show_working_configs_and_addresses.txt` → verification/show commands for all working configs and addressing

## How to apply in Packet Tracer

1. Open `16th.pkt` in Cisco Packet Tracer.
2. Select the RS routers and enter CLI mode.
3. Paste commands from `config_block_0.txt` and `config_block_1.txt`.
4. Apply interface bindings from `interface_example.txt` on the correct interfaces.
5. Verify with:
   - End-to-end `ping` from one device/network to another (required)
   - `show access-lists`
   - `show run | section access-list`
   - `show ip interface <interface>`

For a full demonstration of **all working configs and addresses**, run the command bundle in:

- `show_working_configs_and_addresses.txt`

## Example verification snippet (screenshot)

![Packet Tracer topology ping snippet](https://github.com/user-attachments/assets/cf5e7b59-fa6d-40ea-a5c2-9274f6059685)

These command blocks are aligned with `../Corrected_Tables_3_to_5_and_Cisco_Template.md`.
