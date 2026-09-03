# 01 - Business & Technical Requirements

## 1. Organisation

Apex Financial Services is a medium-sized financial services organisation
with approximately 100 employees.

## 2. Business Requirements

The organisation requires:

- Reliable internal network connectivity
- Internet access
- Departmental network segmentation
- Centralised network services
- Secure administration of network infrastructure
- Guest internet access
- Protection of sensitive systems
- Network and security monitoring
- Logging for security investigations

## 3. Security Requirements

### Network Segmentation

Departments must be separated using VLANs.

### Least Privilege

Users should only have access to resources required for their roles.

### Guest Isolation

Guest devices must not access internal corporate resources.

### Server Protection

Corporate servers must be isolated from ordinary user networks.

### Secure Administration

Network infrastructure must be administered using secure protocols such as SSH.

### Traffic Control

ACLs and security controls must restrict unauthorised communication
between network segments.

### Monitoring and Logging

Relevant network and security events must be logged to support
monitoring and incident investigation.

## 4. Departments

| VLAN | Department |
|------|------------|
| 10 | Management |
| 20 | Finance |
| 30 | HR |
| 40 | IT |
| 50 | Sales |
| 60 | Servers |
| 70 | Guest |
| 99 | Network Management |
