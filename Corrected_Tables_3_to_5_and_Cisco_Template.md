# Corrected Tables 3–5 (Table 1 and Table 2 unchanged)

This file only corrects and cleans **Table 3, Table 4, and Table 5** as requested.  
Table 1 and Table 2 remain unchanged.

## Table 3. Server address assignments (corrected)

Server subnet: **192.167.33.16/28** (mask **255.255.255.240**, usable hosts .17 to .30)

| Server Name | Server IP Address | Subnet Mask | Attached Router Name | Router Interface |
|---|---|---|---|---|
| HTTP Server | 192.167.33.17 | /28 | Core Router | G0/0 |
| DNS Server | 192.167.33.18 | /28 | Core Router | G0/0 |
| SQL Server | 192.167.33.19 | /28 | Core Router | G0/0 |
| Acad Server | 192.167.33.20 | /28 | Academic Router | G0/1 |
| Admin Server | 192.167.33.21 | /28 | Admin Router | G0/1 |
| RS Server | 192.167.33.22 | /28 | Research Router | G0/1 |
| Email Server | 192.167.33.23 | /28 | Core Router | G0/0 |
| Satellite Engineering Lab Server | 192.167.33.24 | /28 | Satellite Engineering Lab Router | G0/1 |

---

## Table 4. Router network/interface and ACL assignment template (corrected)

RS allocations used below are aligned to the provided RS plan:
- 192.167.2.224/27
- 192.167.3.0/27
- 192.167.3.32/27
- 192.167.3.64/27
- 192.167.3.96/27
- 192.167.3.128/27
- 192.167.3.160/28
- 192.167.3.176/28
- 192.167.3.192/28
- 192.167.3.208/28
- 192.167.3.224/28

| Network Name | Router Name | Router Interface | Network # | Subnet Mask | Router IP Address | Access List Number |
|---|---|---|---|---|---|---|
| RS Network | RS S2.1 | G0/0 | 192.167.2.224 | 255.255.255.224 | 192.167.2.225 | 101 (IN) |
| RS Network | RS S2.1 | G1/0 | 192.167.3.0 | 255.255.255.224 | 192.167.3.1 | 101 (IN) |
| RS Network | RS S2.1 | G2/0 | 192.167.3.32 | 255.255.255.224 | 192.167.3.33 | 101 (IN) |
| RS Network | RS S2.2 | G0/0 | 192.167.3.64 | 255.255.255.224 | 192.167.3.65 | 101 (IN) |
| RS Network | RS S2.2 | G1/0 | 192.167.3.96 | 255.255.255.224 | 192.167.3.97 | 101 (IN) |
| RS Network | RS S2.2 | G2/0 | 192.167.3.128 | 255.255.255.224 | 192.167.3.129 | 101 (IN) |
| RS Backbone | RS Core Router | G0/0 | 192.167.33.16 | 255.255.255.240 | 192.167.33.29 | 102 (IN) |

---

## Table 5. Cisco ACL statements (corrected sample)

Acad summary used below: **192.167.2.0/25**  
RS networks used below: **192.167.2.224/27** and **192.167.3.0/24**

| Network | Router Name | Router Interface | Direction | Access-List |
|---|---|---|---|---|
| RS Network | RS S2.2 | G1/0 | In | Extended ACL 101 |
| RS Network | RS Core Router | G0/0 | In | Extended ACL 102 |

### Extended IP access list 101
Permit FTP service from RS to Acad, deny FTP from RS to non-Acad, permit all other IP traffic.

```cisco
ip access-list extended 101
 remark permit FTP service from RS to Acad
 permit tcp 192.167.2.224 0.0.0.31 192.167.2.0 0.0.0.127 eq 21
 permit tcp 192.167.3.0 0.0.0.255 192.167.2.0 0.0.0.127 eq 21
 remark deny FTP service from RS to others
 deny tcp 192.167.2.224 0.0.0.31 any eq 21
 deny tcp 192.167.3.0 0.0.0.255 any eq 21
 remark permit all remaining IP traffic
 permit ip any any
```

### Extended IP access list 102
Permit FTP service from Acad to RS, deny FTP from non-Acad to RS, permit all other IP traffic.

```cisco
ip access-list extended 102
 remark permit FTP service from Acad to RS
 permit tcp 192.167.2.0 0.0.0.127 192.167.2.224 0.0.0.31 eq 21
 permit tcp 192.167.2.0 0.0.0.127 192.167.3.0 0.0.0.255 eq 21
 remark deny FTP service from non-Acad to RS
 deny tcp any 192.167.2.224 0.0.0.31 eq 21
 deny tcp any 192.167.3.0 0.0.0.255 eq 21
 remark permit all remaining IP traffic
 permit ip any any
```

### Cisco interface attachment example

```cisco
interface g1/0
 description RS S2.2 (matches Table 5: ACL 101 on RS S2.2 G1/0)
 ip access-group 101 in

interface g0/0
 description RS core uplink
 ip access-group 102 in
```
