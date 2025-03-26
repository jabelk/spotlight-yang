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

## 🔧 How to Use

1. Load the packages into your NSO environment, ensuring there is no nested directory if you cloned this. 
2. Explore the models in the NSO **GUI** or **CLI**:
   - View and enter data
   - See validation and structure enforced live
3. Try editing the models in VS Code to:
   - Add new fields
   - Modify data types
   - Explore constraints and leaf-list behavior

---

## 📚 Learn More

- [Cisco NSO Dev Center](https://developer.cisco.com/nso/)
- [YANG Language RFC 7950](https://datatracker.ietf.org/doc/html/rfc7950)

