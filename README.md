Enterprise Database Management & Monitoring System
Project Overview
The Enterprise Database Management & Monitoring System is a SQL
Server database administration project built around the
AdventureWorks2022 sample database. The project demonstrates how a
database administrator can manage an enterprise database through
automation, access control, performance optimisation, backup and
recovery, auditing, alerts, and scheduled maintenance.

This was completed as a group project for SCOA031 -- Database
Administration at the University of Limpopo.
Objectives
The project aimed to develop and demonstrate practical database
administration capabilities, including:
- Automating common database operations with stored procedures.
- Applying role-based access control and the principle of least
  privilege.
- Improving query performance through indexing and query optimisation.
- Establishing a backup and recovery strategy.
- Recording data changes for auditing and accountability.
- Sending email alerts for selected database events.
- Automating database integrity checks and index maintenance.
Main Features
1. Stored Procedures and Automation
Six stored procedures were developed for data management and reporting:

Data management - usp_AddNewCustomer -- validates and adds a
customer across related tables within a transaction. -
usp_UpdateProductPrice -- validates and updates a product's list
price. - usp_ArchiveInactiveCustomers -- identifies and archives
customers who have not ordered within a configurable period, with a
preview option.

Reporting - usp_MonthlySalesReport -- reports monthly orders,
unique customers, revenue, and average order value. -
usp_Top10BestSellingProducts -- identifies the ten best-selling
products for a selected date range. - usp_EmployeePerformanceSummary
-- summarises salesperson performance, quota attainment, and ranking.
2. Database Security
Three database roles were created to separate responsibilities:
  Role                                Access purpose
  SalesRole                         Read and write access to the Sales
schema, with read-only access to
relevant Person and Production data

  HRRole                            Read-only access to employee
information and selected person
details
DBA_Role                          Full administrative control
Users were mapped to the appropriate roles, and permissions were tested
using EXECUTE AS USER and REVERT. The design follows the principle
of least privilege.
3. Performance Monitoring and Optimisation
Indexes were added to support common queries involving:
- Sales order date ranges.
- Product name and list-price searches.
- Salesperson and order-date reporting.
- Customer purchase aggregation.
Four queries were also rewritten to improve efficiency. Performance
monitoring procedures were developed to detect long-running queries,
inspect database size, and identify index fragmentation. A
usp_PerformanceDashboard procedure brings these checks together.
4. Backup and Recovery
A backup strategy was implemented using three SQL Server backup types:
- Full backups -- a complete database backup.
- Differential backups -- changes since the most recent full
  backup.
- Transaction log backups -- committed transactions since the
  previous log backup.
The documented schedule uses weekly full backups, daily differential
backups, and transaction log backups every four hours. A restore
demonstration was performed using a separate test database,
AdventureWorks_RestoreTest.
5. Auditing, Triggers, and Email Alerts
An audit table, dbo.AuditTable, records database changes with details
such as the affected table, action type, record ID, SQL login,
timestamp, and description.

Triggers were implemented for Sales.Customer and Production.Product
to capture INSERT, UPDATE, and DELETE operations.

SQL Server Database Mail was configured to alert the DBA about selected
events, including customer or product deletions, sensitive customer data
changes, and product price changes greater than 10%.
6. Maintenance and Server Health
The usp_RunDatabaseMaintenance procedure performs database integrity
checks with DBCC CHECKDB and manages index rebuilding or reorganising
based on fragmentation levels. SQL Server Agent was configured to
schedule this procedure for Sundays at 1:00 AM.
Technology Stack
- Database platform: Microsoft SQL Server
- Sample database: AdventureWorks2022
- Language: Transact-SQL (T-SQL)
- Administration features: Stored procedures, database roles and
  permissions, indexes, triggers, Database Mail, SQL Server Agent,
  backup and restore, and Dynamic Management Views (DMVs)
Skills Demonstrated
- SQL database administration
- T-SQL stored procedure development
- Transactions and error handling with TRY...CATCH
- Role-based access control and permission management
- Query optimisation and index design
- Database performance monitoring
- Backup planning and recovery procedures
- Auditing and event-driven alerts
- Database integrity and maintenance scheduling
Project Context
This project was completed as a collaborative academic database
administration assignment. The implementation and documentation were
based on the AdventureWorks2022 database.
Notes
This README summarises the system described in the project
documentation. To run or reproduce the implementation, the corresponding
SQL scripts, database setup, and configuration details are required.
Email alerts and scheduled jobs also depend on the relevant SQL Server
services and environment configuration.
