Development of a Web and Mobile-Based Order and Installation Management System with Automated Quotation for Urban Blinds

Web and mobile-based order and installation management system for Urban Blinds, a business that provides customized blinds and curtains. It manages customers, products, site measurements, automated quotations, orders, payments, installer schedules, installations, inventory, notifications, dashboards, reports and audit logs — from the first customer inquiry to project completion. Role-based access is provided for the Administrator/Owner, Office Staff, Installers and Customers.

What this is

Urban Blinds currently handles its transactions through Messenger, with records kept in Excel and measurements sometimes written on paper. This project centralizes that process into one system with a structured workflow, automated quotation computation, and installer schedule-conflict detection.

Key Features
Centralized records — customers, product selections, measurements, quotations, orders, payments, schedules and installations in one place.
Product catalog — blinds (priced per square foot) and curtains (priced per panel).
Automated quotation
Blinds: Window Area (sq ft) = Width × Height, then Area × price per square foot
Curtains: Number of panels × price per panel
Delivery and installation are included in the quoted price.
Quotation revision — recalculates the quotation when a customer changes the selected product before approval, while preserving the revision history.
Installer scheduling with conflict detection — compares a proposed measurement or installation date and time against the installer's existing assignments and flags overlaps. Non-overlapping slots on the same day are allowed.
Payment monitoring — records the required 50% down payment (Cash, GCash or Bank) and computes the remaining balance. Material preparation is blocked until the down payment is recorded.
Order workflow tracking
Material and inventory monitoring, with supplier, purchase and damage records.
Notifications, dashboard and operational reports
Audit logs for significant system activities.
Role-based access control
Order Workflow
Customer Inquiry → Product Selection → Measurement Scheduling → Site Measurement →
Quotation Preparation → Customer Decision → 50% Down Payment → Material Preparation →
Installation Scheduling → Installation → Final Payment → Completed

At the customer decision stage, the customer may approve the quotation, request a product change (the quotation is revised), or cancel the transaction.

User Roles
Role	What they do
Administrator / Owner	Manages users, roles, products and pricing; monitors customers, orders, payments, installer schedules and inventory; views reports and audit logs.
Office Staff	Manages customers and orders, schedules measurements and installations, generates and revises quotations, records payments, monitors materials and inventory, updates order status, generates reports.
Installer	Views assigned schedules and customer details, records site measurements, updates measurement and installation status, records installation completion.
Customer	Registers/logs in, browses the catalog, sends inquiries, views and approves quotations, requests product changes, cancels orders, views schedule, tracks order and payment status.
System Architecture

The system follows a three-layer architecture:

Presentation Layer — Web application and mobile application (dashboard, customer interface, quotation interface, order tracking, installer schedule, inventory, reports).
Business Logic Layer — Authentication and RBAC, customer/product management, measurement processing, Automated Quotation Engine (sq ft and price calculation), Scheduling Engine (installer availability and conflict detection), Order Workflow Engine, payment/balance processing, inventory monitoring, notification processing, reporting and audit logging. Communicates with the presentation layer over HTTPS/API.
Data Layer — Relational database.
Database

The database is urbanblinds_db (MySQL / MariaDB), exported from phpMyAdmin. It contains 30 tables:

Area	Tables
Users and access	admins, staff, installers, user_account, audit_logs
Customers	customers
Products	products, blinds, curtains
Measurement	measurement_schedules, measurements
Quotation	quotations, quotation_items, revisions
Orders	orders, order_items
Payments	payments, cash_payment_details, gcash_payment_details, bank_payment_details
Installation	installation_schedules, installations
Inventory and sales	inventory_items, damages, suppliers, purchases, purchase_items, sales, sale_items

The full schema and sample data are in the database folder.

Import the database
Start Apache and MySQL in XAMPP.
Open phpMyAdmin at http://localhost/phpmyadmin.
Create a database named urbanblinds_db (collation utf8mb4_general_ci).
Select it, go to Import, and choose database/urbanblinds_db.sql.
Click Go.

Or from the command line:

bash
mysql -u root -p -e "CREATE DATABASE urbanblinds_db CHARACTER SET utf8mb4;"
mysql -u root -p urbanblinds_db < database/urbanblinds_db.sql
Tech Stack
Layer	Technology
UI/UX Design	Figma
Web Platform	(to be finalized)
Mobile Platform	(to be finalized)
Backend	(to be finalized)
Database	MySQL / MariaDB (XAMPP)
Reporting and Analytics	Charting and reporting tools
Methodology
Developmental Research approach for designing, developing, testing and evaluating the system.
Agile software development with incremental delivery based on requirements, testing results and stakeholder feedback.
Testing: functional tests for quotation computation, schedule-conflict detection, status transitions, authentication and payment balance computation; followed by user evaluation on functionality, usability, efficiency, reliability and security.
Sample Test Cases

Blind quotation — 5 ft × 6 ft at ₱200/sq ft → 30 sq ft × ₱200 = ₱6,000

Curtain quotation — 4 panels × ₱1,400/panel = ₱5,600

Installer conflict — Installer A is booked on September 20, 2026, 9:00–11:00 AM.

Requested slot	Expected result
10:00 AM – 12:00 PM	Overlap detected, installer unavailable
1:00 PM – 3:00 PM	Allowed, no overlap
Scope and Delimitation

The system does not include:

Full payroll and salary processing
Direct integration with banks or online payment gateways (payments are recorded by authorized personnel)
GPS tracking of installers, biometric attendance, or automated manufacturing equipment
Automatic posting of completed projects to social media (photo use remains subject to customer consent)
Repository Structure
├── database/
│   └── urbanblinds_db.sql
└── README.md
