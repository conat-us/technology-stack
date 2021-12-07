# technology-stack
Description of the Conatus technology stack and strategy

# Introduction

The Conatus product line will be implemented with technologies and libraries provided by or built upon the Microsoft .NET platform. 

# Application Development Language

C# will be used as the application development language for Conatus, due to its modernity and productivity. The version of the language selected will be the latest version of the language supported by the underlying .NET platform. For .NET 5 this will be C# version 9. For .NET 6 this will be C# version 10.

# .NET Platform

In late 2021 through to March 2022, all development of Conatus will take place using .NET 5. This is because all of the tooling associated with .NET 5 is mature and stable.

The Conatus product line will be re-platformed to .NET 6 in late March or early April 2022. This will coincide with the launch (by Microsoft) of a stable and full-featured version of Visual Studio 2022 for Mac. The rationale for this is that software development will take place on MacBook Pros and iMac workstations. The latest Visual Studio 2022 for Mac is in Beta only and is still relatively unusable.

# Development Tools

The following development tools will be used for software development of Conatus:

- Microsoft Visual Studio 2019 (through to late March/April 2022) 32-bit
- Microsoft Visual Studio 2022 (from April 2022) 64-bit

Either Mac or Windows versions or Visual Studio are permissible since the software is highly consistent across platforms for the features of the .NET platform that Conatus will use.

# Data Persistence

The Conatus product line is suitable for use with a relational data model and an object relational mapping framework (ORM). 

## Object Relational Mapping (ORM)

The ORM product that will be used for the Conatus product line will be Microsoft's Entity Framework Core. This ORM isolates application developers - at least to a large extent - from the details of the underlying database product. In other words, the semantics of CRUD operations from an application developer's standpoint are dictated by the ORM product rather than the dialect of SQL used by the underlying relational database management system. This means that the application development team can develop business logic that has a dependency on the ORM framework with the added benefit that the underlying database product can be swapped for another at a later date with relatively little impact.

Development of the Conatus product line will be based upon Entity Framework Core version 5 until late March/April 2022. From April 2022 Entity Framework Core version 6 will be used. This transition will coincide with the adoption of .NET 6 and the Visual Studio 2022.

## Relational Database

Entity Framework Core comes with out of the box support for the following relational database products:

- SQLite
- PostgreSQL
- MySQL
- Microsoft SQL Server

All of these are excellent relational database products. SQLite is unique within this group because it can be embedded in a product and run entirely within memory, whereas the other relational database management systems are all database servers.

Development of the Conatus product line will use two database products:

SQLite will be used for initial development of new features and development of unit tests where data persistence and retrieval is required using Entity Framework Core. The reason for this is that SQLLite can be run in memory and is very, very fast. As a result, automated build times that incorporate unit testing in the Continuous Integration / Continuous Deployment (CI/CD) pipeline are able to run quickly and are not prone to failing due to stale test data that was persisted on a remote database server.

The production relational database will be PosgreSQL. The selection of this product is due to its scalability, maturity and ubiquity. PostgreSQL is offered by virtually all Infrastructure-as-a-Service (IaaS) vendors, is cost effective (being cheaper than other proprietary products), is well supported (with skills being readily available), is ideally suited to native deployment on Linux distributions (with which it is usually shipped as standard), is robust, reliable, scalable and enterprise grade. Furthermore, enhanced relational database products (such as AWS Aurora) are based upon and compatible with PostgreSQL syntax.

