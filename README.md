# Oracle Pluggable Database (PDB) Management — Individual Assignment II

- **Student Name:** Pierrine
- **Student ID:** 26283


## 1. Overview of the assignment tasks

This assignment demonstrates the management of Oracle Pluggable Databases (PDBs) using Oracle Database 21c XE.

The objectives completed were:

1. Creating a new Pluggable Database (PDB) and database user.
2. Creating and deleting a temporary PDB.
3. Accessing Oracle Enterprise Manager (OEM) and demonstrating the Oracle environment.
4. Documenting the completed activities with screenshots.

---

## 2. Oracle Environment Used

- **Database:** XE
- **Oracle Version:** 21.3.0.0.0 Express Edition
- **Host:** localhost
- **Tool used for sql**: Oracle SQL Developer
- **Port:** 1522
- **Main PDB:** PI_PDB_26283
- **Database User:** Pierrine_plsqlauca_26283

The main PDB was created from the existing XEPDB1 PDB.

---

## 3. Task 1 — Create a New PDB and User

### PDB Creation

A new PDB named `pi_pdb_26283` was created from `XEPDB1`.

Because the Oracle environment required explicit datafile conversion, the `FILE_NAME_CONVERT` clause was used during creation.

The PDB was opened successfully and verified as:

```text
PI_PDB_26283    READ WRITE

### Database User Creation

A database user named `Pierrine_plsqlauca_26283` was created inside the `pi_pdb_26283` PDB.

The user was granted the `CREATE SESSION` privilege so that the account could connect to the database.

The account was verified successfully as:

```text
PIERRINE_PLSQLAUCA_26283    OPEN
```

### Task 1 Evidence

The screenshots for this task demonstrate:

- Creation of `pi_pdb_26283`
- Opening of the PDB
- Creation of `Pierrine_plsqlauca_26283`
- Verification that the user account is OPEN

---

## 4. Task 2 — Create and Delete a Temporary PDB

### Temporary PDB Creation

A temporary PDB named:

```text
pi_to_delete_pdb_26283
```

was created from the existing `XEPDB1` PDB.

The temporary PDB was successfully created and appeared in the PDB list.

### Temporary PDB Deletion

After confirming that the temporary PDB had been created successfully, it was deleted using:

```sql
DROP PLUGGABLE DATABASE pi_to_delete_pdb_26283 INCLUDING DATAFILES;
```

The `INCLUDING DATAFILES` option was used to remove the associated datafiles together with the PDB.

The PDB list was then checked using:

```sql
SHOW PDBS;
```

The temporary PDB was no longer present in the list, confirming that it had been successfully deleted.

### Task 2 Evidence

The screenshots for this task demonstrate:

- Creation of `pi_to_delete_pdb_26283` 
- Deletion of the temporary PDB
- Final verification showing that the temporary PDB was no longer listed

---

## 5. Task 3 — Oracle Enterprise Manager (OEM)

Oracle Enterprise Manager Database Express was accessed successfully using the Oracle HTTPS service.

The OEM dashboard was accessed using the database user:

```text
PIERRINE_PLSQLAUCA_26283
```

within the:

```text
PI_PDB_26283
```

PDB.

The OEM dashboard displayed the Oracle environment and provided information about the database, performance, services, storage, and resources.

The dashboard showed:

- Oracle Enterprise Manager Database Express
- `XE / PI_PDB_26283`
- Oracle Database version `21.3.0.0.0`
- The username `pierrine_plsqlauca_26283`
- Database status and performance information

The Resources section also displayed information such as:

- CPU Usage
- Active Sessions
- Memory
- Data Storage
- SQL Monitor

### Task 3 Evidence

The screenshots for this task demonstrate that:

1. Oracle Enterprise Manager is accessible.
2. The dashboard reflects the Oracle environment used in the assignment.
3. The dashboard reflects the `PI_PDB_26283` PDB environment.
4. The assignment username `pierrine_plsqlauca_26283` is visible on the dashboard.

---

## 6. Final PDB Status

The final PDB environment was verified using SQL Developer.

The final PDB list showed:

```text
PDB$SEED          READ ONLY
XEPDB1            READ WRITE
PI_PDB_26283      READ WRITE
```

This confirmed that the main assignment PDB remained available and open.

The temporary PDB:

```text
PI_TO_DELETE_PDB_26283
```

was successfully deleted and was no longer present in the final PDB list.

---

## 7. Challenges Encountered and Solutions

### Challenge 1 — PDB creation required FILE_NAME_CONVERT

The initial attempt to create the PDB without specifying file conversion resulted in an error requiring the `FILE_NAME_CONVERT` clause.

#### Solution

The existing XEPDB1 datafile locations were identified and the `FILE_NAME_CONVERT` clause was used to create the new PDB with separate datafiles.

---

### Challenge 2 — Insufficient privileges

The initial attempt to create the PDB using the SYSTEM account resulted in insufficient privileges.

#### Solution

The database was accessed using the SYS account with the SYSDBA role for PDB administration.

---

### Challenge 3 — OEM username visibility

Initially, Oracle Enterprise Manager displayed the `SYS` account when accessing the dashboard.

#### Solution

The assignment database user was granted the required OEM Express read-only privilege. OEM was then accessed using the assignment user within `PI_PDB_26283`. After logging in with the assignment user, the username became visible on the OEM dashboard.

---

## 8. Conclusion

The required Oracle Pluggable Database management activities were completed successfully.

A new PDB named `pi_pdb_26283` was created from `XEPDB1` and opened successfully. The required database user `Pierrine_plsqlauca_26283` was created and verified as OPEN.

A temporary PDB named `pi_to_delete_pdb_26283` was also created and subsequently deleted, including its associated datafiles.

Oracle Enterprise Manager Database Express was successfully accessed and used to demonstrate the Oracle environment, the assignment PDB, database resources, and the assignment username.

Screenshots included in this repository provide evidence of the completed tasks.
---

## Submission Details

- **Repository Link:** https://github.com/Pierrine83/oracle_pdb_ass_II_26283_pierrine
- **PDB Name Created:** `pi_pdb_26283`
- **Issues Encountered:** Yes
