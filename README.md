# Project 10: Internal DNS Setup

## Project Overview

This project demonstrates the configuration of an internal DNS server using Windows Server 2025. The objective is to create a DNS A record and verify hostname-to-IP address resolution using the `nslookup` command.

## Objective

- Configure an internal DNS server.
- Create a Forward Lookup Zone.
- Create an A record for a web server.
- Verify DNS resolution using `nslookup`.
- Capture screenshots as evidence.

## Technologies Used

- Microsoft Azure
- Windows Server 2025 Datacenter
- DNS Server
- Active Directory Domain Services (AD DS)
- Windows PowerShell
- Azure Bastion

## Infrastructure Details

| Component | Configuration |
|---|---|
| Virtual Machine | p9-dc |
| Operating System | Windows Server 2025 |
| Domain Name | lab.example.test |
| DNS Server IP | 10.0.0.5 |
| DNS Zone | lab.example.test |
| DNS Record Type | A (Host) |
| Hostname | web.lab.example.test |
| Configured IP Address | 192.0.2.10 |

**Note:** `192.0.2.10` is a reserved documentation address used for DNS testing. It does not represent an actual deployed web server.

## Implementation Steps

### Step 1: Configure DNS Server

1. Connected to the Windows Server VM using Azure Bastion.
2. Installed Active Directory Domain Services.
3. Promoted the server to a Domain Controller.
4. Installed and configured the DNS Server role.
5. Verified that the DNS service was running.

### Step 2: Configure DNS Zone

1. Opened Server Manager.
2. Navigated to **Tools → DNS**.
3. Expanded the DNS server `p9-dc`.
4. Opened **Forward Lookup Zones**.
5. Selected the existing zone `lab.example.test`.

### Step 3: Create DNS A Record

Created an A record with the following configuration:

- **Name:** web
- **Fully Qualified Domain Name:** web.lab.example.test
- **Record Type:** A
- **IPv4 Address:** 192.0.2.10

### Step 4: Verify DNS Resolution

Opened Windows PowerShell and executed:

```powershell
nslookup web.lab.example.test 10.0.0.5
```

**Result:**

```text
Server:  p9-dc.internal.cloudapp.net
Address: 10.0.0.5

Name:    web.lab.example.test
Address: 192.0.2.10
```

The DNS server successfully resolved the hostname to the configured IPv4 address.

## Testing Results

| Test Case | Result |
|---|---|
| DNS Server installed | Passed |
| DNS Service running | Passed |
| Forward Lookup Zone available | Passed |
| A record created | Passed |
| nslookup resolution | Passed |
| Actual web server connectivity | Not tested |

## Evidence

### DNS A Record Configuration

![DNS A Record](screenshots/project10-dns-record.png)

### Successful nslookup Verification

![nslookup Verification](screenshots/project10-nslookup.png)

## Key Learnings

- Understanding DNS and hostname resolution.
- Configuring DNS on Windows Server.
- Managing Forward Lookup Zones.
- Creating DNS A records.
- Verifying DNS resolution using `nslookup`.
- Understanding the relationship between Active Directory and DNS.

## Conclusion

Successfully configured an internal DNS server using Windows Server 2025, created a DNS A record, and verified hostname resolution using `nslookup`.

The project demonstrates internal DNS name resolution. Since the A record points to a reserved test address, connectivity to a real web application was not demonstrated.
