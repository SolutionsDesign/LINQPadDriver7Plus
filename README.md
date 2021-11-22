LLBLGen Pro LINQPad Driver for LINQPad v7+
===========================
The Official [LLBLGen Pro](https://www.llblgen.com) LINQPad driver for LINQPad v7+, built on .NET 6. This driver is to be used with 
assemblies compiled against .NET 6 or .NET Standard 2.0+.

### Supported databases and generated code
The generated code has to be built against .NET Standard 2.0 or higher. The supported databases are:

* MS Access
* DB2
* Firebird
* Oracle (using managed ODP.NET)
* PostgreSQL
* SQL Server.

The driver will pull the necessary ADO.NET provider packages from NuGet, hence there's no MySQL support.

### Executing SQL
The driver isn't designed to be used to execute SQL against a database, though it will work if the following
is true:
- You specify a connection string in the connection dialog
- In the connection string specified you connect to a SQL Server service.

### Executing QuerySpec or Low-level API queries
Set the 'language' combo box in the query pane in LINQpad to 'C# Statements' or 'VB.NET statements'. Be sure to select
the right connection as well.

Specify the query as-is. To see results, use the `Dump();` extension method by appending it to the 
results. 

For Adapter, obtain the adapter from the property 'AdapterToUse'. See the example below:

```C#
// Queryspec:
var qf = new QueryFactory();
var results = this.AdapterToUse.FetchQuery(qf.Customer);
results.Dump();

// Low level api:
var managers = new EntityCollection<ManagerEntity>();
this.AdapterToUse.FetchEntityCollection(managers, null);
managers.Dump();
```