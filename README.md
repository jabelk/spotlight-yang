# Learning YANG Data Modeling with Cisco NSO

This repo contains the demo YANG models used in the session **"Learning YANG Data Modeling with Cisco NSO"**.

These examples are designed to help you understand the core concepts of YANG and how they come to life inside NSO — across both GUI and CLI.

## 📦 What’s Included

### 1. `learn-yang`
A simple introductory model to show:
- Containers (`person`)
- Leaf nodes (`name`, `age`, `favorite-color`)
- Basic data types (`string`, `uint32`)

Great for understanding the fundamentals of YANG syntax and structure.

---

### 2. `router`
Introduces:
- Input validation using regex (IPv4 address)
- Mandatory fields
- Status fields like `oper-status`

This model demonstrates how YANG enforces data quality through constraints.

---

### 3. `person-skills`
Expands on the first two by showing:
- `list` structures (`skill-list` with `name`, `proficiency`, `time-spent`)
- `enumeration` values for `proficiency` (beginner, intermediate, advanced)
- `leaf-list` usage (`hobbies`)

A great example for modeling repeatable data structures in a scalable way.

---

### 4. `interface-mode-config`
Demonstrates:
- `choice` between access or trunk mode
- `leaf` and `leaf-list` with enforced VLAN range (`1..4094`)

This model mirrors real-world switchport logic — enforcing that a port is either in access or trunk mode, not both.

---

### 5. `employee-checkin`
A non-networking model that highlights:
- `grouping` and `uses` to reuse person attributes
- A `must` constraint to ensure `checkin-time` is set only when `checked-in` is `true`
- Use of `default` and `mandatory` to enforce clean logic

It’s a great example for applying YANG outside of infrastructure — modeling real-world policies and intent.


## 🔧 How to Use

1. Load the packages into your NSO environment, ensuring there is no nested directory if you cloned this. 
2. Explore the models in the NSO **GUI** or **CLI**:
   - View and enter data
   - See validation and structure enforced live
3. Try editing the models in VS Code to:
   - Add new fields
   - Modify data types
   - Explore constraints and leaf-list behavior

Sample Commands

```
# Demo CLI Script for YANG Model Validation

# learn-yang (basic container and leaf types)
learn-yang person name Alice age 30 favorite-color Blue
commit

# router (regex IP address validation)
router name R1 address 192.168.1.1 oper-status up
commit

# This will fail due to invalid IP format
router name R2 address not-an-ip oper-status down
commit

# person-skills (list, leaf-list, enum)
skills person-name Bob
skills skill-list YANG proficiency beginner time-spent 30
skills hobbies Reading
skills hobbies Coding
commit

# This will fail due to invalid enum value
skills skill-list JSON proficiency expert
commit

# interface-mode-config (choice with range)
 (choice with range)
interface-config interface gi0/1 interface-name gi0/1 access-vlan 10
commit

interface-config interface gi0/2 interface-name gi0/2 allowed-vlans 10 allowed-vlans 20
commit

# This will fail due to VLAN number out of range
interface-config interface gi0/3 interface-name gi0/3 access-vlan 5000
commit

# employee-checkin (grouping + must)
employee-status name Alice role Engineer checked-in true checkin-time 09:00
commit

# This will fail due to missing checkin-time when checked-in is true
employee-status name Bob role Analyst checked-in true
commit


```


---

## 📚 Learn More

- [Cisco NSO Dev Center](https://developer.cisco.com/nso/)
- [YANG Language RFC 7950](https://datatracker.ietf.org/doc/html/rfc7950)

