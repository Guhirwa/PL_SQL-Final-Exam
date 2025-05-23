# 💼 Financial and Economic Planning Management System (FEPMS)

## 📌 Overview

The **Financial and Economic Planning Management System (FEPMS)** is an Oracle-based solution designed to automate and centralize financial operations, including budgeting, expenditure tracking, revenue management, vendor engagement, and project cost management. It supports multiple departments and roles, offering real-time data visibility, audit logs, and high transaction scalability.

---

## 📍 Phase I: Problem Definition & Scope

### 1️⃣ Problem Definition

Many organizations rely on **manual financial tracking**, resulting in:

- ❌ Error-prone processes
- ❌ Delayed visibility into financial status
- ❌ Siloed departmental systems
- ❌ Weak compliance and audit trails

**FEPMS addresses these with:**

- ✅ Real-time budget monitoring
- ✅ Automated expenditure and revenue tracking
- ✅ Vendor and project cost integration
- ✅ Compliance-ready audit logs

### 2️⃣ Context: Where & How the System Will Be Used

| **Industry**     | **Key Use Cases**                                                     |
|------------------|----------------------------------------------------------------------|
| Universities     | Manage department budgets, research grants, and vendor payments       |
| Hospitals        | Track medical supply expenditures and public/private funding          |
| Government       | Oversee project budgeting, contractor payments, and tax allocations   |
| Corporations     | Forecast financials and manage vendor/departmental cost centers       |

### 3️⃣ Target Users

| **User Role**         | **Key Benefits**                                                                 |
|-----------------------|---------------------------------------------------------------------------------|
| Finance Teams         | Automated reports, budget alerts, audit readiness                               |
| Department Heads      | Live budget usage, project-specific cost visibility                             |
| Vendors & Creditors   | Transparent transaction tracking, automated payment status updates              |
| Auditors & Compliance | Full transaction history, immutable audit logs                                  |
| Senior Management     | Financial dashboards and performance forecasting                                |

### 4️⃣ Project Goals

#### 🅐 Automation & Efficiency
- ✅ Replace spreadsheets with real-time budget monitoring
- ✅ Auto-calculate remaining funds, debts, and project expenses
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

## 📍 Phase IV: Oracle Database Configuration

### ✅ Task 1: Create & Configure Pluggable Database (PDB)

**Database Name:** `mon_26750_christian_FEPMS_db`  
**Admin User:** `christian_admin1`  
**Password:** `christian`

**Steps Followed**:
1. Connected to Oracle as SYSDBA.
2. Created PDB with `FILE_NAME_CONVERT` for isolated file storage.
3. Opened the PDB to make it active.
4. Saved database state for automatic startup on reboot.
5. Switched session to PDB to begin schema development.
6. Verified PDB status to ensure successful setup.

### ✅ Task 2: Monitor with Oracle Enterprise Manager (OEM)

**Access OEM via Docker:**  
🔗 `https://localhost:36011/em`

**Login Details:**
- **Username:** `system`
- **Password:** `9188`
- **Container/PDB Name:** `mon_26750_christian_FEPMS_DB`

**OEM Management Includes:**
- 📊 **Storage Usage Monitoring**: Tablespace allocation
- 👥 **User Sessions**: Connections overview
- ⚙️ **Real-time Performance Metrics**: CPU, I/O
- 🚨 **System Alerts**: Health checks and warnings
- 💡 **PDB Health Status**: Operational verification

OEM provides centralized performance monitoring and administrative operations for FEPMS in a user-friendly interface.

---

## 📍 Phase V: Table Implementation and Data Insertion

### Overview

This phase implemented the physical database structure based on the logical design. All tables were created in Oracle Database, ensuring proper data types, primary and foreign keys, constraints, and normalization to maintain **data integrity, consistency, and reliability**. The structure supports the full scope of FEPMS, enabling management of budgeting, expenditures, revenue, debts, projects, employees, vendors, and user accounts.

> **Note**: Data insertion is planned for a later phase, but the structure is ready to accept realistic data for testing.

### Table Creation Descriptions and Column Purposes

1. **Vendor**
   - **Purpose**: Stores vendor information for goods/services.
   - **Columns**:
     - `VendorID`: Unique identifier
     - `VendorName`: Vendor name
     - `VendorContact`: Unique contact number
     - `Email`: Unique email
     - `Address`: Vendor address
     - `EntryDate`: Registration timestamp

2. **Budget**
   - **Purpose**: Tracks annual budgets.
   - **Columns**:
     - `BudgetID`: Unique identifier
     - `BudgetYear`: Fiscal year (2020–2050)
     - `TotalBudget`: Budget amount (> 0)
     - `EntryDate`: Record timestamp

3. **Departments**
   - **Purpose**: Represents organizational departments.
   - **Columns**:
     - `DepartmentID`: Unique identifier
     - `DepartmentName`: Unique department name

4. **Expenditure_Category**
   - **Purpose**: Classifies expenditure purposes.
   - **Columns**:
     - `CategoryID`: Unique identifier
     - `CategoryPurpose`: Expenditure purpose

5. **Expenditure**
   - **Purpose**: Records spending activities.
   - **Columns**:
     - `ExpenditureID`: Unique identifier
     - `BudgetID`: Linked budget
     - `DepartmentID`: Responsible department
     - `CategoryID`: Expenditure category
     - `ExpenditureAmount`: Amount spent (> 0)
     - `ExpenditureDate`: Spending date
     - `EntryDate`: Record timestamp

6. **Roles**
   - **Purpose**: Defines organizational roles.
   - **Columns**:
     - `RoleID`: Unique identifier
     - `RolePosition`: Unique role name

7. **Employee**
   - **Purpose**: Stores employee details.
   - **Columns**:
     - `EmployeeID`: Unique identifier
     - `EmployeeName`: Full name
     - `RoleID`: Assigned role
     - `DepartmentID`: Assigned department
     - `Email`: Unique email
     - `Contact`: Unique contact number
     - `Address`: Employee address

8. **Revenue_Sources**
   - **Purpose**: Tracks income sources.
   - **Columns**:
     - `SourceID`: Unique identifier
     - `SourceName`: Unique source name

9. **Revenue**
   - **Purpose**: Records income transactions.
   - **Columns**:
     - `RevenueID`: Unique identifier
     - `BudgetID`: Linked budget
     - `SourceID`: Revenue source
     - `RevenueAmount`: Amount received (> 0)
     - `RevenueDate`: Receipt date
     - `EntryDate`: Record timestamp

10. **Creditors**
    - **Purpose**: Tracks entities owed money.
    - **Columns**:
      - `CreditorID`: Unique identifier
      - `CreditorName`: Unique name
      - `Email`: Unique email
      - `Address`: Creditor address

11. **Debt**
    - **Purpose**: Tracks borrowed funds.
    - **Columns**:
      - `DebtID`: Unique identifier
      - `BudgetID`: Linked budget
      - `CreditorID`: Linked creditor
      - `DebtAmount`: Amount borrowed (> 0)
      - `DueDate`: Payment due date
      - `DebtStatus`: Status (Pending, Paid, Overdue)
      - `EntryDate`: Record timestamp

12. **Project**
    - **Purpose**: Manages organizational projects.
    - **Columns**:
      - `ProjectID`: Unique identifier
      - `ProjectName`: Project name
      - `ProjectDescription`: Project details
      - `StartDate`: Start date
      - `EndDate`: Completion date
      - `ProjectStatus`: Status (e.g., Planned, Ongoing)
      - `ManagerID`: Responsible employee
      - `EntryDate`: Record timestamp

13. **Vendor_Services**
    - **Purpose**: Tracks vendor services.
    - **Columns**:
      - `ServiceID`: Unique identifier
      - `VendorID`: Linked vendor
      - `ServiceName`: Service name

14. **Project_Vendor**
    - **Purpose**: Links vendors to projects.
    - **Columns**:
      - `P_V`: Unique identifier
      - `ProjectID`: Linked project
      - `VendorID`: Linked vendor

15. **Users**
    - **Purpose**: Manages user accounts.
    - **Columns**:
      - `UserID`: Unique identifier
      - `Username`: Unique login name
      - `Password`: Account password
      - `EmployeeID`: Linked employee
      - `AccountType`: Role (e.g., Admin, User)
      - `Status`: Approval status (Pending, Approved, Declined)

16. **History_Log**
    - **Purpose**: Logs record changes for auditing.
    - **Columns**:
      - `LogID`: Unique identifier
      - `TableName`: Affected table
      - `RecordID`: Affected record ID
      - `Action`: Change type (Insert, Update, Delete)
      - `OldValues`: Previous data (CLOB)
      - `NewValues`: Updated data (CLOB)
      - `ChangedBy`: User who made the change
      - `ChangeDateTime`: Change timestamp

### ✔️ How I Met the Phase V Requirements

#### ✅ 1. Table Creation
All tables were implemented using Oracle SQL, aligning with the logical data model.

#### ✅ 2. Physical Structure
Ensured:
- Appropriate **data types** (e.g., `VARCHAR2`, `NUMBER`, `CLOB`, `DATE`, `TIMESTAMP`)
- Defined **primary and foreign keys** for relational integrity
- Applied **constraints** (`NOT NULL`, `UNIQUE`, `CHECK`)

#### ✅ 3. Data Integrity
Constraints and foreign keys ensure accurate, logically connected data (e.g., no duplicate budgets, valid references for revenue/expenditure).

#### ✅ 4. Ready for Data Insertion
Tables are prepared for realistic data insertion in future phases for testing and demonstration.

This phase delivers a robust, scalable database structure aligned with FEPMS goals.

---

## 📍 Phase VI: PL/SQL Implementation and Analytics

### Part I: [Placeholder for Your Content]
*To be filled by Christian GUHIRWA.*

---

### Part II: Financial Analytics Procedures and Functions

This section details the procedures and functions in the `financial_analytics` and `advanced_analytics` PL/SQL packages for the Financial Analytics System. Each entry includes the call syntax, a description of what the procedure/function does, its purpose, and a placeholder for the output screenshot. The system analyzes financial performance, including budget utilization, expenditure trends, revenue sources, project efficiency, and fiscal health.

#### Prerequisites
- Oracle Database with the schema, triggers, and packages (`financial_analytics` and `advanced_analytics`) set up.
- SQL client (e.g., SQL*Plus, SQL Developer) with `SET SERVEROUTPUT ON` to view `DBMS_OUTPUT` results.
- Sample data in the database (use the commented-out inserts in the test script or your own data).

#### Procedures and Functions

##### financial_analytics Package

1. **calculate_dept_budget_utilization**

   **Call Syntax**:
   ```sql
   DECLARE
       v_utilization NUMBER;
   BEGIN
       v_utilization := financial_analytics.calculate_dept_budget_utilization('DEPT001', 2024);
       DBMS_OUTPUT.PUT_LINE('Utilization: ' || TO_CHAR(v_utilization, '990.99') || '%');
   END;
   /
   ```

   **Description**:
   - **What**: Calculates the percentage of the total budget used by a specified department in a given year.
   - **How**: Retrieves the total budget for the year and sums expenditures for the department, then computes the percentage. Handles cases where no expenditure data exists (returns 0).
   - **Why**: Helps management assess whether a department is over- or under-spending, critical for budget allocation and financial oversight.
   - **Exception Handling**: Raises errors for missing budget data or query issues.

   **Output Screenshot**:
   ![Output of calculate_dept_budget_utilization](screenshots/calculate_dept_budget_utilization_screenshot.png)

2. **get_financial_health_status**

   **Call Syntax**:
   ```sql
   DECLARE
       v_status VARCHAR2(30);
   BEGIN
       v_status := financial_analytics.get_financial_health_status(95.5);
       DBMS_OUTPUT.PUT_LINE('Financial Health Status: ' || v_status);
   END;
   /
   ```

   **Description**:
   - **What**: Returns a financial health status based on a budget utilization percentage.
   - **How**: Categorizes the percentage into `OVER BUDGET` (>100%), `WARNING` (90–100%), `OPTIMAL` (70–90%), `UNDER UTILIZED` (40–70%), or `SEVERELY UNDER UTILIZED` (<40%).
   - **Why**: Provides a quick, interpretable status for management to prioritize interventions (e.g., addressing overspending).
   - **Exception Handling**: None, as it’s a simple conditional check.

   **Output Screenshot**:
   ![Output of get_financial_health_status](screenshots/get_financial_health_status_screenshot.png)

3. **generate_dept_expenditure_report**

   **Call Syntax**:
   ```sql
   BEGIN
       financial_analytics.generate_dept_expenditure_report('DEPT001', 2024);
   END;
   /
   ```

   **Description**:
   - **What**: Generates a detailed report of a department’s expenditures by category for a given year.
   - **How**: Uses a cursor with window functions (`SUM`, `RANK`) to compute category totals, percentages of total department spending, and expense rankings. Outputs a formatted report with the department name, budget utilization, financial health status, and category breakdown.
   - **Why**: Identifies high-spending categories, aiding resource allocation and cost control.
   - **Exception Handling**: Handles missing department data and query errors.

   **Output Screenshot**:
   ![Output of generate_dept_expenditure_report](screenshots/dept_expenditure_report_screenshot.png)

4. **analyze_revenue_sources**

   **Call Syntax**:
   ```sql
   BEGIN
       financial_analytics.analyze_revenue_sources(2024);
   END;
   /
   ```

   **Description**:
   - **What**: Analyzes revenue sources for a specified fiscal year.
   - **How**: Uses a cursor with window functions (`SUM`, `ROW_NUMBER`) to compute total revenue per source, percentage of total revenue, cumulative percentage, and ranking. Outputs a report with total budget, total revenue, revenue-to-budget ratio, and source details.
   - **Why**: Identifies key revenue streams and their efficiency, supporting strategic financial planning.
   - **Exception Handling**: Handles missing budget or revenue data.

   **Output Screenshot**:
   ![Output of analyze_revenue_sources](screenshots/revenue_sources_analysis_screenshot.png)

5. **find_over_budget_projects**

   **Call Syntax**:
   ```sql
   BEGIN
       financial_analytics.find_over_budget_projects;
   END;
   /
   ```

   **Description**:
   - **What**: Identifies projects that exceed their allocated budgets.
   - **How**: Uses a cursor with a CTE and window functions (`RANK`) to compare project expenditures to simulated budget allocations (based on project status: 90% for Completed, 70% for Ongoing, 50% for others). Outputs a report with project details, expenditure, budget, variance, utilization percentage, and ranking.
   - **Why**: Helps management address cost overruns and improve project budgeting.
   - **Exception Handling**: Handles query errors.
   - **Note**: Assumes expenditures link to projects via `CategoryID`, which may need adjustment based on your schema.

   **Output Screenshot**:
   ![Output of find_over_budget_projects](screenshots/over_budget_projects_screenshot.png)

6. **track_monthly_expenditure_trends**

   **Call Syntax**:
   ```sql
   BEGIN
       financial_analytics.track_monthly_expenditure_trends(2024);
   END;
   /
   ```

   **Description**:
   - **What**: Tracks monthly expenditure trends for a fiscal year.
   - **How**: Uses a cursor with window functions (`LAG`, `SUM`, `AVG`) to compute monthly totals, month-over-month changes, percentage changes, cumulative totals, and three-month moving averages. Outputs a report with total annual budget, monthly details, year-to-date total, remaining budget, and utilization.
   - **Why**: Reveals spending patterns and trends, aiding forecasting and budget adjustments.
   - **Exception Handling**: Handles missing budget data and query errors.

   **Output Screenshot**:
   ![Output of track_monthly_expenditure_trends](screenshots/monthly_expenditure_trends_screenshot.png)

##### advanced_analytics Package

7. **analyze_dept_spending_patterns**

   **Call Syntax**:
   ```sql
   BEGIN
       advanced_analytics.analyze_dept_spending_patterns('DEPT001');
       advanced_analytics.analyze_dept_spending_patterns(NULL); -- For all departments
   END;
   /
   ```

   **Description**:
   - **What**: Analyzes spending patterns for a specific department or all departments.
   - **How**: Uses a cursor with window functions (`AVG`, `LAG`) to compute monthly spending, average monthly spending (same month across years), percentage deviation from average, three-month moving averages, and year-over-year growth. Outputs a report grouped by department and year.
   - **Why**: Identifies seasonal trends and anomalies in spending, supporting long-term planning.
   - **Exception Handling**: Handles missing department data and query errors.

   **Output Screenshots**:
   ![Output of analyze_dept_spending_patterns (DEPT001)](screenshots/dept_spending_patterns_screenshot.png)
   ![Output of analyze_dept_spending_patterns (All Departments)](screenshots/dept_spending_patterns_all_screenshot.png)

8. **identify_top_vendors**

   **Call Syntax**:
   ```sql
   BEGIN
       advanced_analytics.identify_top_vendors(5);
   END;
   /
   ```

   **Description**:
   - **What**: Identifies the top vendors by project engagement.
   - **How**: Uses a cursor with window functions (`RANK`, `DENSE_RANK`, `ROW_NUMBER`, `NTILE`) to compute project and service counts, engagement percentage (relative to total projects), and rankings. Outputs a report of the top N vendors with quartile indicators.
   - **Why**: Prioritizes vendor relationships based on their project involvement, aiding procurement decisions.
   - **Exception Handling**: Handles query errors.

   **Output Screenshot**:
   ![Output of identify_top_vendors](screenshots/top_vendors_screenshot.png)

9. **calculate_debt_to_revenue_ratio**

   **Call Syntax**:
   ```sql
   DECLARE
       v_ratio NUMBER;
   BEGIN
       v_ratio := advanced_analytics.calculate_debt_to_revenue_ratio(2024);
       DBMS_OUTPUT.PUT_LINE('Debt-to-Revenue Ratio: ' || TO_CHAR(v_ratio, '0.999'));
   END;
   /
   ```

   **Description**:
   - **What**: Calculates the debt-to-revenue ratio for a fiscal year.
   - **How**: Computes total debt and revenue, returning their ratio (or NULL if revenue is zero). Handles cases with no data.
   - **Why**: Assesses financial stability by comparing debt to revenue, critical for risk management.
   - **Exception Handling**: Handles missing data and query errors.

   **Output Screenshot**:
   ![Output of calculate_dept_budget_utilization](screenshots/debt_to_revenue_ratio_screenshot.png)

10. **generate_fiscal_health_dashboard**

    **Call Syntax**:
    ```sql
    BEGIN
        advanced_analytics.generate_fiscal_health_dashboard(2024);
    END;
    /
    ```

    **Description**:
    - **What**: Generates a comprehensive fiscal health dashboard for a fiscal year.
    - **How**: Uses a cursor with window functions (`RANK`, `PERCENT_RANK`) to compute department budget utilization, total budget, expenditure, revenue, debt-to-revenue ratio, and a fiscal health score (0–100). Outputs a dashboard with overall metrics and department breakdowns, categorizing health as EXCELLENT, GOOD, MODERATE, CONCERN, or CRITICAL.
    - **Why**: Provides a holistic view of organizational financial health, supporting strategic decisions.
    - **Exception Handling**: Handles missing budget data and query errors.

    **Output Screenshot**:
    ![Output of generate_fiscal_health_dashboard](screenshots/fiscal_health_dashboard_screenshot.png)

11. **forecast_expenditures**

    **Call Syntax**:
    ```sql
    BEGIN
        advanced_analytics.forecast_expenditures(6);
    END;
    /
    ```

    **Description**:
    - **What**: Forecasts expenditures for a specified number of months.
    - **How**: Uses a cursor with window functions (`AVG`, `LAG`) to analyze historical expenditure patterns. Generates forecasts using year-over-year growth, weighted moving averages, or three-month moving averages, selecting the best method based on data availability. Outputs a report with forecast months, base values, predicted values, and methods.
    - **Why**: Enables proactive budget planning by predicting future spending.
    - **Exception Handling**: Handles query errors and missing historical data.

    **Output Screenshot**:
    ![Output of forecast_expenditures](screenshots/expenditure_forecast_screenshot.png)

#### End-to-End Test

**Call Syntax**:
```sql
BEGIN
    display_test_banner('End-to-End Analytics Suite Test');
    DBMS_OUTPUT.PUT_LINE('Running full analytics suite...');
    financial_analytics.track_monthly_expenditure_trends(2024);
    financial_analytics.analyze_revenue_sources(2024);
    financial_analytics.find_over_budget_projects;
    financial_analytics.generate_dept_expenditure_report('DEPT001', 2024);
    advanced_analytics.analyze_dept_spending_patterns('DEPT001');
    advanced_analytics.analyze_dept_spending_patterns(NULL);
    advanced_analytics.identify_top_vendors(5);
    advanced_analytics.generate_fiscal_health_dashboard(2024);
    advanced_analytics.forecast_expenditures(6);
    DECLARE
        v_ratio NUMBER;
    BEGIN
        v_ratio := advanced_analytics.calculate_debt_to_revenue_ratio(2024);
        DBMS_OUTPUT.PUT_LINE('Debt-to-Revenue Ratio for 2024: ' || TO_CHAR(v_ratio, '0.999'));
    END;
    DBMS_OUTPUT.PUT_LINE('End-to-End Analytics Suite Test Completed Successfully');
EXCEPTION
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('Error in end-to-end analytics suite: ' || SQLERRM);
END;
/
```

**Description**:
- **What**: Runs all procedures and functions in sequence to test the entire analytics suite.
- **How**: Calls each procedure/function with sample parameters (e.g., Department ID `DEPT001`, Budget Year 2024), displaying results via `DBMS_OUTPUT`. Includes a helper procedure (`display_test_banner`) for formatting.
- **Why**: Ensures all components work together cohesively, validating the system’s reliability and correctness.
- **Exception Handling**: Catches and reports any errors during execution.

**Output Screenshot**:
![Output of End-to-End Analytics Suite Test](screenshots/end_to_end_test_screenshot.png)

#### Instructions for Capturing Screenshots
1. **Set Up Database**: Ensure the database has the schema, triggers, packages, and sample data (use the test script’s commented-out inserts or your own data).
2. **Run Each Call**: Execute the call syntax for each procedure/function in an SQL client with `SET SERVEROUTPUT ON`. For example:
   ```sql
   SET SERVEROUTPUT ON SIZE 1000000;
   BEGIN
       financial_analytics.generate_dept_expenditure_report('DEPT001', 2024);
   END;
   /
   ```
3. **Capture Outputs**: Take screenshots of the `DBMS_OUTPUT` results for each call and the end-to-end test. Save them in a `screenshots/` directory with the filenames specified above (e.g., `dept_expenditure_report_screenshot.png`).
4. **Use Screenshots**: Include these screenshots in documentation (e.g., the LaTeX report or a repository) to visualize the outputs.

---

## 📦 Technologies Used

- **Database**: Oracle 21c (Pluggable Architecture)
- **Monitoring**: Oracle Enterprise Manager (OEM)
- **Containerization**: Docker / Oracle-db Image
- **Future Innovation**: Front-end design (planned)

---

## 🙌 Author

**Christian GUHIRWA [mon_26750]**  
FEPMS Oracle Database Developer & System Architect

---