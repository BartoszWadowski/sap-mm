# Waste Disposal Process – SAP MM

This document describes the logistics and purchasing process for handling medical waste collection and disposal in a SAP MM environment. The scenario is based on a company cooperating with veterinary clinics, hospitals, and other medical institutions.

---

## 🌐 Business Flow Overview

1. **Client Request** – A medical client (e.g. veterinary clinic) requests pickup of waste.
2. **Purchase Requisition (PR)** – A PR is created for material `ODPAD-MED` (medical waste).
3. **Purchase Order (PO)** – A PO is generated and assigned to an internal disposal unit.
4. **Goods Receipt (MIGO)** – Waste is received into a temporary storage location.
5. **Warehouse Storage** – Waste is held in plant `MI00`, location `ZMED`.
6. **Disposal Transport** – Goods are issued and transported to the incineration facility.
7. **Final Consumption** – Waste is removed from inventory (movement type 261 or 551).

---

## 🗂 SAP Transaction Mapping

| Process Step              | SAP Transaction | Notes                                  |
|---------------------------|------------------|----------------------------------------|
| Create PR                 | ME51N            | Material: `ODPAD-MED`, Plant: `MI00`   |
| Convert to PO             | ME21N            | Vendor: internal or disposal unit      |
| Perform Goods Receipt     | MIGO             | Movement type 101                      |
| Track Stock Levels        | MM60, MB52       | Check for `ZMED` location              |
| Transfer/Issue to disposal| MB1A / MIGO      | Movement type 261 or 551               |
| View full history         | ME80FN, ME80RN   | Analyze document flow                  |

---

## 📦 Master Data Used

- **Material**: `ODPAD-MED` (Medical Waste)
- **Vendors**:
  - 700001 – Klinika Weterynaryjna Alfa
  - 700002 – Szpital Wojewódzki Beta
- **Plant**: `MI00`
- **Storage Location**: `ZMED`

---

## 📌 Remarks

- Ensure movement types are allowed for the material type.
- This process allows full SAP MM traceability from request to disposal.
- Can be extended to include WM, QM or compliance monitoring.


