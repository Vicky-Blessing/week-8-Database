# Clinic Management System Project Documentation

## 📌Project Title
Clinic Management Sysytem (CMS)

## 📑Description
This project is a relational database designed for managing a medical clinic. It stores and organizes:

> - Patient records (personal info, medical history)
> - Doctor schedules & specialties
> - Appointments & medical diagnoses
> - Prescriptions & medications
> - Billing & insurance information
> - Lab tests & staff management

Built with MySQL, it ensures data integrity through foreign keys, constraints, and normalized tables.

## ⚙️ Setup & Installation
> - Prerequisites
MySQL Server (or MariaDB)

MySQL Workbench (or any SQL client)

> - Database Setup
Option 1: Using MySQL Workbench

Open MySQL Workbench

Create a new schema named ClinicManagement

Copy & run the SQL script (provided earlier) to create tables

Run the sample data script to populate the database

Option 2: Command Line

sh
mysql -u root -p
CREATE DATABASE ClinicManagement;
USE ClinicManagement;
-- Paste the SQL table creation script here
-- Then paste the sample data insertion script

Option 3: Import SQL File
Save the SQL script as clinic_management.sql

Import via:

sh
mysql -u username -p ClinicManagement < clinic_management.sql

## 📂 Database Tables Summary

Table	Description
> - Patients-Stores patient personal & contact info
> - Doctors-Doctor details & specialties
> - Appointments-Links patients & doctors
> - MedicalRecords-Patient health history
> - Diagnoses-Medical conditions identified
> - Medications-List of available drugs
> - Prescriptions-Doctor-prescribed medications
> - InsuranceProviders-Patient insurance details
> - Billing-Clinic invoices & payments
> - DoctorSchedules-Doctor availability
> - Staff-Non-doctor employees
> - LabTests-Medical test results

## 🔎 Sample Queries
> - Get All Appointments for a Patient
sql
SELECT p.first_name, p.last_name, a.appointment_date, d.first_name AS doctor_name
FROM Patients p
JOIN Appointments a ON p.patient_id = a.patient_id
JOIN Doctors d ON a.doctor_id = d.doctor_id
WHERE p.patient_id = 1;

> - List All Prescriptions for a Patient
sql
SELECT m.name AS medication, pr.dosage, pr.frequency, d.first_name AS prescribed_by
FROM Prescriptions pr
JOIN Medications m ON pr.medication_id = m.medication_id
JOIN Doctors d ON pr.doctor_id = d.doctor_id
WHERE pr.record_id IN (SELECT record_id FROM MedicalRecords WHERE patient_id = 1);

> - Find Pending Lab Tests
sql
SELECT p.first_name, p.last_name, lt.test_name, lt.test_date
FROM LabTests lt
JOIN Patients p ON lt.patient_id = p.patient_id
WHERE lt.status = 'Pending';

## 📜 License
This project is open-source under the MIT License.

## 📬 Contact
For questions or improvements, feel free to reach out!
marthyvickyblessing@gmail.com


🚀 Happy Coding!







