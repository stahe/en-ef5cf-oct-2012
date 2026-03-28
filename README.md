# Migrating from NHibernate to Entity Framework 5 (October 2012)

This document illustrates a **flexible and scalable ASP.NET application architecture**
and shows how to replace the **NHibernate** ORM with **Entity Framework 5**
without modifying the application layer.

🌐 The associated website can be accessed at: https://stahe.github.io/en-ef5cf-oct-2012/

---

## Background

**Entity Framework** is an ORM (Object Relational Mapper) originally created by Microsoft
and made open source in July 2012.

In an ASP.NET course, this document is based on a layered architecture
that allows technologies (ORM, DBMS) to be updated without affecting the application.

---

## General architecture

The diagram below shows the architectures used in the application:

![ASP.NET architecture with NHibernate and Spring.NET](https://stahe.github.io/ef5cf-oct-2012/images/10000000000007D200000183315F4E40.png)

![ASP.NET architecture with Entity Framework 5 and Spring.NET](https://stahe.github.io/ef5cf-oct-2012/images/10000000000007D7000001825B1CF7DD.png)

### Description of the layers

- **ASP.NET Application**  
  Presentation and business logic layer.

- **DAO (Data Access Objects)**  
  Data access interface used by the application.

- **ORM (NHibernate / Entity Framework)**  
  Responsible for generating SQL and communicating with ADO.NET.

- **ADO.NET**  
  Connector to the DBMS.

- **DBMS**  
  Database management system.

- **Spring.NET**  
  Ensures layer integration and dependency injection.

---

## Why use an ORM?

Linking the DAO layer directly to ADO.NET makes the application dependent on the DBMS:

- differences in data types;
- proprietary SQL;
- DBMS-specific libraries.

With an ORM, changing the DBMS essentially amounts to **changing the configuration**
of the ORM. The DAO layer remains unchanged.

---

## Role of Spring.NET

Spring.NET allows:

- the ASP.NET application to obtain a reference to the DAO layer;
- the creation of this layer from a configuration file;
- the replacement of one DAO implementation with another **without modifying the code**,
  provided the interface remains the same.

---

## Purpose of this document

To demonstrate in practice that the architecture:

- is **resilient to changes in DBMS**;
- is **resilient to changes in ORM**;
- allows **NHibernate to be replaced by Entity Framework 5**
  without modifying the ASP.NET application layer.

---

## Approach followed

The migration is carried out in several stages:

1. Exploring **Entity Framework 5** with several DBMS;
2. Building a new data access layer (**DAO2**);
3. Connecting the existing ASP.NET application to this new DAO layer.

---

## Target audience

- ASP.NET developers
- Students and lecturers in software architecture
- Anyone interested in decoupled and scalable architectures

---

## Licence and usage

Educational document intended for teaching and demonstrating
scalable application architectures.
