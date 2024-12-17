# healthcare-management
Healthcare Management involves overseeing, administration, organization and coordinating healthcare services to ensure efficient, quality care.  The goal is to provide effective healthcare while optimizing resources and reducing costs.

Tasks performed

1. Creating Database Schema:
Define and create the schema (healthcare_management) to organize and store various tables related to healthcare data, such as patients, medical staff, appointments, etc.

CREATE SCHEMA healthcare_management;

2. Table Creation:
Create tables for storing different types of healthcare-related data such as patient information, medical history, doctor schedules, and appointment details.
Example:

CREATE TABLE healthcare_management.patient_info (
    patient_id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    gender VARCHAR(10),
    date_of_birth DATE,
    address VARCHAR(200)
);

3. Inserting Data into Tables:
Insert sample or real data into these tables using INSERT INTO statements. This includes adding information like patient names, appointments, medical records, etc.
Example:

INSERT INTO healthcare_management.patient_info (name, gender, date_of_birth, address)
VALUES ('Zihaio', 'Male', '1980-07-15', '123 Main Street, City');

4. Establishing Relationships between Tables:
Use foreign keys to link tables, ensuring that related data (e.g., patient details, doctor appointments) can be associated with each other.
Example:

CREATE TABLE healthcare_management.appointments (
    appointment_id SERIAL PRIMARY KEY,
    patient_id INT,
    doctor_id INT,
    appointment_date DATE,
    appointment_time TIME,
    FOREIGN KEY (patient_id) REFERENCES healthcare_management.patient_info(patient_id)
);

5.Managing User Authentication:

Create tables for managing user login details (e.g., healthcare staff), such as their usernames, passwords, and roles.
Example:

CREATE TABLE healthcare_management.user_login (
    user_id TEXT PRIMARY KEY,
    user_password TEXT,
    user_role VARCHAR(50)
);

6. Querying Data for Patient and Appointment Information:
 
Use SELECT queries to retrieve specific data, such as details of patient appointments, medical history, or doctor availability.
Example:

SELECT name, appointment_date, appointment_time
FROM healthcare_management.appointments
JOIN healthcare_management.patient_info ON healthcare_management.appointments.patient_id = healthcare_management.patient_info.patient_id
WHERE patient_info.name = 'John Doe';

7. Updating Data:

Use UPDATE statements to modify existing data, such as changing patient details or updating appointment times.
Example:

UPDATE healthcare_management.patient_info
SET address = '456 New Address, City'
WHERE patient_id = 1;

8. Deleting Data:

Use DELETE statements to remove outdated or incorrect records, such as deleting canceled appointments or patient records that are no longer needed.
Example:

DELETE FROM healthcare_management.appointments WHERE appointment_id = 1;

9. Generating Reports:

Use SELECT queries with aggregate functions like COUNT(), SUM(), or AVG() to generate reports on metrics like the number of appointments, average visit duration, or staff performance.
Example:

SELECT doctor_id, COUNT(appointment_id) AS total_appointments
FROM healthcare_management.appointments
GROUP BY doctor_id;

10. Data Integrity and Constraints:

Apply data integrity rules through constraints (e.g., NOT NULL, UNIQUE, CHECK) to ensure valid and consistent data across the tables.
Example:

ALTER TABLE healthcare_management.patient_info
ADD CONSTRAINT check_patient_age CHECK (age >= 18);

These tasks help in organizing, managing, and manipulating healthcare data effectively within a relational database, ensuring accurate and efficient data management for healthcare providers.
