# Corporate Notebook Management Database

![SQL](https://img.shields.io/badge/SQL-2563EB?style=flat-square) ![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)

**Main portfolio project — collaborative database system.** Developed at Senac Santana by **César de Oliveira Zanelatto, Kleber Amaro da Silva, and Rafael Sper Moralli**. This repository is a fork of [CesarZanelatto/ProjetoBancodeDados](https://github.com/CesarZanelatto/ProjetoBancodeDados).

## Overview

A MySQL database for managing corporate notebooks, employees, and departments. Its purpose is to identify who is using each notebook, which department they belong to, and which devices are available.

## Scope

- Employee, department, and notebook registration.
- Notebook assignment and return operations.
- Equipment lookup and reports through views.
- Stored procedures, transactions, and security scripts.

## Scripts

- [Database creation](ProjetoDB/CriacaoDoDB.sql)
- [Tables and relationships](ProjetoDB/Tabelas.sql)
- [Stored procedures](ProjetoDB/Procedures.sql)
- [Views](ProjetoDB/Views.sql)
- [Transactions](ProjetoDB/Transacoes.sql)
- [Security](ProjetoDB/Seguranca.sql)
- [Test data and inserts](ProjetoDB/Testes%20e%20Inserts.sql)

## Data model

- **Departments (`setor`)** store a department ID, name, and description.
- **Employees (`FUNCIONARIO`)** store identity and contact information and reference a department.
- **Notebooks (`NOTEBOOK`)** store asset and serial numbers, hardware specifications, acquisition date, availability, and an optional responsible employee.

The SQL identifiers retain their original Portuguese names. Refer to [Tabelas.sql](ProjetoDB/Tabelas.sql) for the implemented field types and constraints.

## Business rules

1. Each employee belongs to one department; a department may have multiple employees.
2. Each notebook can be assigned to only one employee at a time.
3. An employee may receive registered notebooks.
4. Asset numbers and serial numbers must be unique.
5. Available notebooks may have no responsible employee.

## Procedures and views

The project documentation describes employee procedures such as `inserirFuncionario()`, `buscarFuncionario()`, and `quantidadeFuncionarios()`, and notebook procedures such as `inserirNotebook()`, `buscarNotebook()`, `quantidadeNotebooks()`, and `categoriaNotebook()`.

Assignment and return operations are represented by `atribuirNotebook()` and `devolverNotebook()`. The documented views include:

- `view_notebooks_detalhado` — notebook, employee, role, and department details.
- `view_notebooks_disponiveis` — available devices.
- `vw_notebooks_por_setor` — totals and availability by department.

Consult the linked SQL scripts for their definitions and execution requirements.

## Transactions and security

The assignment workflow checks the notebook, its availability, and the employee before updating the device and committing the operation. The return workflow removes the responsible employee and marks the notebook as available.

The security script contains database-user and permission examples, along with AES encryption/decryption examples. Use the source scripts to inspect the implemented security operations and their relationship with the table definitions.

## Local setup

Use a local MySQL installation and a SQL client such as MySQL Workbench. XAMPP was also used in the project environment.

```sh
git clone https://github.com/Kleber720/ProjetoBancodeDados.git
cd ProjetoBancodeDados
```

Open the SQL files in your client. Create the database first, then the tables. Review the procedures, views, transactions, security, and test-data scripts before running the operations you need.

### Backup and restore

The original Windows/XAMPP workflow uses:

```bat
"C:\xampp\mysql\bin\mysqldump.exe" -u root ProjetoDB > backup.sql
"C:\xampp\mysql\bin\mysql.exe" -u root ProjetoDB < backup.sql
```

## Modeling approach

The project documentation discusses normalization through 1NF, 2NF, and 3NF: atomic values, dependencies on primary keys, and separation of entities to reduce transitive dependencies.

## Diagrams

### Use-case diagram

The IT administrator manages employees and notebooks, checks reports, and controls equipment assignments.

<img width="413" height="548" alt="Corporate notebook management use-case diagram" src="https://github.com/user-attachments/assets/602b5420-e4fa-42f0-a579-f312f608d027" />

### Entity-relationship diagram

The diagram shows entities, relationships, cardinalities, primary keys, and foreign keys.

<img width="571" height="467" alt="Corporate notebook management entity-relationship diagram" src="https://github.com/user-attachments/assets/88a32d73-d5b5-42f7-8278-78af26753024" />

## Skills applied

Relational database modeling, SQL, referential integrity, stored procedures, transactions, reporting views, and collaborative development.


---

[Kleber Amaro’s portfolio](https://github.com/Kleber720) · [All repositories](https://github.com/Kleber720?tab=repositories)
