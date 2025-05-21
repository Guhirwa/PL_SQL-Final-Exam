# 💼 Financial and Economic Planning Management System (FEPMS)

## 📌 Overview

The **Financial and Economic Planning Management System (FEPMS)** is an Oracle-based solution designed to automate and centralize financial operations such as budgeting, expenditures, revenue tracking, vendor engagement, and project cost management. It supports multiple departments and roles, offering real-time data visibility, audit logs, and high transaction scalability.

---

## 📍 PHASE I: Problem Definition & Scope

### 1️⃣ Problem Definition

Many organizations still rely on **manual financial tracking**, leading to:

- ❌ Error-prone processes
- ❌ Delayed visibility into financial status
- ❌ Siloed departmental systems
- ❌ Weak compliance and audit trails

**FEPMS addresses these with:**

✔ Real-time budget monitoring  
✔ Automated expenditure & revenue tracking  
✔ Vendor & project cost integration  
✔ Compliance-ready audit logs

---

### 2️⃣ Context: Where & How the System Will Be Used

| **Industry**     | **Key Use Cases**                                                     |
|------------------|------------------------------------------------------------------------|
| Universities     | Manage department budgets, research grants, and vendor payments        |
| Hospitals        | Track medical supply expenditures and public/private funding           |
| Government       | Oversee project budgeting, contractor payments, and tax allocations    |
| Corporations     | Forecast financials and manage vendor/departmental cost centers        |

---

### 3️⃣ Target Users

| **User Role**         | **Key Benefits**                                                                 |
|------------------------|----------------------------------------------------------------------------------|
| Finance Teams         | Automated reports, budget alerts, audit readiness                                |
| Department Heads      | Live budget usage, project-specific cost visibility                              |
| Vendors & Creditors   | Transparent transaction tracking, automated payment status updates               |
| Auditors & Compliance | Full transaction history, immutable audit logs                                   |
| Senior Management     | Financial dashboards and performance forecasting                                 |

---

### 4️⃣ Project Goals

#### 🅐 Automation & Efficiency
- ✅ Replace spreadsheets with real-time budget monitoring
- ✅ Auto-calculate remaining funds, debts, project expenses
- ✅ Generate scheduled weekly/monthly reports

#### 🅑 Accuracy & Transparency
- ✅ Trigger alerts near budget thresholds
- ✅ Track vendor payments to avoid duplication/overdue issues
- ✅ Break down project costs: labor, materials, vendors

#### 🅒 Security & Compliance
- ✅ Role-based access control
- ✅ Immutable change logs (who/what/when/why)
- ✅ Data encryption for sensitive transactions

#### 🅓 Scalability
- ✅ Optimized for 10,000+ transactions/day
- ✅ Multi-department budget support (e.g., HR, R&D, Ops)
- ✅ Cloud-ready access for remote teams

🔗 [📽️ Phase I Presentation](https://docs.google.com/presentation/d/12En0MH6jekl9C7prdO2AvWtm-AVOfvgc/edit?usp=drive_link&ouid=101458021040637784897&rtpof=true&sd=true)

---

## 📍 PHASE IV: Oracle Database Configuration

### ✅ Task 1: Create & Configure Pluggable Database (PDB)

**Database Name:** `mon_26750_christian_FEPMS_db`  
**Admin User:** `christian_admin1`  
**Password:** `christian`

Steps followed:

1. **Connected to Oracle as SYSDBA**
2. **Created PDB** with `FILE_NAME_CONVERT` for isolated file storage
3. **Opened the PDB** to make it active
4. **Saved database state** for automatic startup on reboot
5. **Switched session to PDB** to begin schema development
6. **Verified PDB status** to ensure successful setup

---

### ✅ Task 2: Monitor with Oracle Enterprise Manager (OEM)

**Access OEM via Docker:**  
🔗 `https://localhost:36011/em`

**Login Details:**
- **Username:** `system`
- **Password:** `9188`
- **Container/PDB Name:** `mon_26750_christian_FEPMS_DB`

OEM Management Includes:
- 📊 **Storage Usage Monitoring** (Tablespace allocation)
- 👥 **User Sessions** (Connections overview)
- ⚙️ **Real-time Performance Metrics** (CPU, I/O)
- 🚨 **System Alerts** (Health checks and warnings)
- 💡 **PDB Health Status** (Operational verification)

OEM enables centralized performance monitoring and administrative operations for FEPMS in a user-friendly interface.

---

## 📦 Technologies Used

- **Database:** Oracle 21c (Pluggable Architecture)
- **Monitoring:** Oracle Enterprise Manager (OEM)
- **Containerization:** Docker / Oracle-db Image
- **Future Innovation refinement:** Front-End design

---

## 🙌 Author

**Christian GUHIRWA [mon_26750]**  
FEPMS Oracle Database Developer & System Architect

---

