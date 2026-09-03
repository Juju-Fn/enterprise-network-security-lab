# 02 - Network Design

## 1. Network Architecture

Apex Financial Services will use a hierarchical network architecture consisting
of an edge router, a Layer 3 core switch, access switches, servers, and
endpoint devices.

The architecture is designed to provide network segmentation, controlled
communication between departments, secure administration, and scalability.

## 2. Device Inventory

| Device | Quantity | Purpose |
|--------|----------|---------|
| Cisco Router | 1 | Internet/WAN gateway |
| Layer 3 Core Switch | 1 | Inter-VLAN routing and core connectivity |
| Access Switch | 2 | Connect endpoint devices |
| Server | 3 | Infrastructure and application services |
| Employee PCs | 10+ | Represent departmental users |
| Guest Device | 1+ | Represent guest users |
| Security Testing Device | 1 | Controlled security testing |

## 3. VLAN Design

| VLAN | Name | Network | Gateway |
|------|------|---------|---------|
| 10 | Management | 10.10.10.0/24 | 10.10.10.1 |
| 20 | Finance | 10.10.20.0/24 | 10.10.20.1 |
| 30 | HR | 10.10.30.0/24 | 10.10.30.1 |
| 40 | IT | 10.10.40.0/24 | 10.10.40.1 |
| 50 | Sales | 10.10.50.0/24 | 10.10.50.1 |
| 60 | Servers | 10.10.60.0/24 | 10.10.60.1 |
| 70 | Guest | 10.10.70.0/24 | 10.10.70.1 |
| 99 | Network Management | 10.10.99.0/24 | 10.10.99.1 |

## 4. Network Zones

### User Zone

The user zone contains the Management, Finance, HR, IT, and Sales VLANs.

Users are separated into different VLANs to reduce unnecessary
communication between departments and limit the impact of a compromised
endpoint.

### Server Zone

The Server VLAN contains infrastructure and application servers.

Access to this network will be restricted using appropriate security controls.

### Guest Zone

The Guest VLAN is intended for visitors and unmanaged devices.

Guest devices must not be able to access internal corporate resources.

### Network Management Zone

The Network Management VLAN is dedicated to the administration of network
infrastructure.

Only authorised administrators should be permitted to access management
interfaces.

## 5. Routing Architecture

The Layer 3 core switch will provide inter-VLAN routing.

The core switch will act as the default gateway for the internal VLANs.

The edge router will provide connectivity between the internal network and
the external/WAN network.

## 6. Security Boundaries

Traffic between VLANs will be controlled using access control policies.

The following restrictions will be implemented:

- Guest users must not access internal corporate VLANs.
- User networks should only access required server services.
- Sensitive departmental networks should not have unrestricted access to
  other departments.
- Network device management should be restricted to authorised administrators.
- Server access should be limited according to business requirements.

## 7. Secure Administration

Network infrastructure will be configured for secure remote administration
using SSH.

Insecure management protocols will be avoided where possible.

Administrative access will be restricted to the Network Management VLAN.

## 8. High-Level Topology

```text
                         INTERNET
                            |
                       +----+----+
                       |  Router |
                       +----+----+
                            |
                       +----+----+
                       |   Core  |
                       | L3 Switch|
                       +----+----+
                            |
              +-------------+-------------+
              |                           |
        +-----+------+              +-----+------+
        | Access SW1 |              | Access SW2 |
        +-----+------+              +-----+------+
              |                           |
        +-----+-----+               +-----+-----+
        |           |               |           |
      Users       Users           Users       Guest
     VLANs       VLANs           VLANs      VLAN 70

                            |
                       +----+----+
                       | Servers  |
                       | VLAN 60  |
                       +---------+

                 Network Management
                      VLAN 99
