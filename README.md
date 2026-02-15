## Student Information
- Name: Eugene
- Student ID: 27087

# 1. Overview of Tasks

This project demonstrates practical administration of Oracle Multitenant Architecture.  
The following tasks were completed:

1. Creation of a Pluggable Database (PDB)
2. Creation of a local user inside the PDB
3. Creation and deletion of a temporary PDB
4. Configuration and access of Oracle Enterprise Manager (OEM)

All naming conventions were strictly followed as required.

# 2. Oracle Environment Used

- Oracle Database Version: Oracle 19c (Enterprise Edition) *(Adjust if different)*
- Architecture: Multitenant (CDB + PDB)
- Access Tool: SQL*Plus
- OEM: Oracle Enterprise Manager Express
- Operating System: Windows *(or Linux if applicable)*

The environment consisted of:
- Container Database (CDB)
- Pluggable Databases (PDBs)
- SYSDBA administrative access
- 
# 3. Task Explanations

## Task 1: Create a Pluggable Database

PDB Name:
eu_pdb_2024101

User Created Inside PDB:
eugene_plsqlauca_2024101

Steps Performed:
- Connected as SYSDBA
- Created PDB using CREATE PLUGGABLE DATABASE
- Opened PDB in READ WRITE mode
- Switched session to the new PDB
- Created local user
- Granted CONNECT and RESOURCE privileges
- Verified user creation using DBA_USERS

Result:
PDB was successfully created and configured .

## Task 2: Create and Delete Temporary PDB

Temporary PDB Name:
eu_to_delete_pdb_2024101

Steps Performed:
- Created temporary PDB
- Verified existence using V$PDBS
- Closed PDB using CLOSE IMMEDIATE
- Dropped PDB including datafiles
- Verified deletion

Result:
Temporary PDB was completely removed from the system.

## Task 3: Configure and Access Oracle Enterprise Manager (OEM)

Steps Performed:
- Verified HTTPS port using DBMS_XDB_CONFIG
- Configured HTTPS port (5500)
- Accessed OEM through browser
- Logged in as SYSDBA
- Verified:
  - Database environment
  - Existing PDB (eu_pdb_2024101)
  - Created user visibility

Result:
OEM dashboard successfully reflected the configured environment.

# 4. Challenges Faced and Solutions

### Challenge 1: ORA-65096 Error (Invalid Common User)
Cause:
Attempted to create a local user inside CDB$ROOT.

Solution:
Switched to the correct PDB using:
ALTER SESSION SET CONTAINER = eu_pdb_2024101;

### Challenge 2: Insufficient Privileges Error
Cause:
Not connected as SYSDBA.

Solution:
Reconnected using:
sqlplus / as sysdba

### Challenge 3: OEM Not Opening
Cause:
HTTPS port not configured.

Solution:
Configured port using:
EXEC DBMS_XDB_CONFIG.SETHTTPSPORT(5500);

# 5. Integrity Statement

I confirm that this project was completed independently and follows the required naming conventions and technical guidelines. All SQL commands were executed and verified within my Oracle environment.

Student Name: Eugene  
Student ID: 2024101  
Date: (Insert Date)
