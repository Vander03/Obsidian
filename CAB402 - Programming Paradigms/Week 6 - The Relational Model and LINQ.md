A relation is a homogeneous *set* of records, each record consisting of a heterogeneous (multiple types) set of uniquely named attributes.

Relations can be of the following kinds:
- Base Relations are those which are stored directly
- Derived Relations (also known as Views)

![[Pasted image 20250412222835.png|500]]

## 1 Rational Algebra (Abstract like Lambda)
The result of any and all of these operations are **also relations**
- **Restrict** is a unary operation which allows the selection of a subset of the records in a relation according to some desired criteria (filter)
- **Project** is a unary operation which creates a new relation corresponding to the old relation with various attributes removed from the records (select in SQL)
- **Product** is a binary operation corresponding to the cartesian product of mathematics 
- (join two relations, AND in SQL. It is also unconditional all rows are combined)
- **Union** is a binary operation which creates a relation consisting of all records in either argument relation
- **Intersection** is a binary operation which creates a relation consisting of all records in both argument relations
- **Difference** is a binary operation which creates a relation consisting of all records in the first but not the second argument relation
- **Join** is a binary operation which constructs all possible records that result from matching identical attributes of the records of the argument relations
- **Divide** is a ternary operation which returns all records of the first argument which occur in the second argument associated with each record of the third argument
- One significant benefit of this manipulation language (aside from its simplicity) is that it has the property of **closure** — that all operands and results are of the same kind (relations) — hence the operations can be nested in arbitrary ways.

## 2 SQL (Structured Query Language)
```SQL
SELECT WORKDEPT, MAX(SALARY)
FROM DSN8A10.EMP Q
GROUP BY WORKDEPT
HAVING MAX(SALARY) < (SELECT AVG(SALARY)
						FROM DSN8A10.EMP
						WHERE NOT WORKDEPT = Q.WORKDEPT);
```

## 3 Object-Relational Mapping Framework
![[Pasted image 20250412223342.png]]

## 4 Object-Relational Impedance Mismatch
![[Pasted image 20250412223431.png]]

## 5 Impedance Mismatches
![[Pasted image 20250412223648.png|400]]

## 6 LINQ (Language Integrated Query)
https://msdn.microsoft.com/en-us/library/bb397926.aspx
- Native syntax for expressing queries in C# and VB.NET
- All data is object-oriented and strongly typed
- Bridges to Relational and XML data providing a universal query language for all types of data.

### 6.1 Data Sources
Anything that implements a `IEnumerable` interface, including:
- Results from other LINQ queries
- Standard collection classes (System.Collection.List, Array)
- Specialised LINQ providers
	- LINQ to SQL
	- LINQ to XML
	- LINQ to ADO.NET

### 6.2 LINQ Example
![[Pasted image 20250412223837.png|500]]

### 6.3 LINQ with Type Inference
![[Pasted image 20250412223908.png|500]]


### 6.4 LINQ Types
![[Pasted image 20250501222257.png]]

### 6.5 LINQ Projection
![[Pasted image 20250412224235.png]]

### 6.6 LINQ Filtering
![[Pasted image 20250412224659.png|500]]

### 6.7 LINQ Ordering
![[Pasted image 20250412224729.png|300]]

### 6.8 LINQ Grouping
![[Pasted image 20250412224814.png]]

### 6.9 LINQ Joining
![[Pasted image 20250412224850.png]]

#### 6.9.1 Relationships without Join
If the database has foreign key constraints then navigation properties will be created automatically.
- Handles both 1-to-1 and 1-to-many relationships.

![[Pasted image 20250412225013.png]]

### 6.10 LINQ: Query Syntax vs Method Syntax
![[Pasted image 20250412225112.png]]

### 6.11 LINQ Custom Providers
LINQ: Custom Providers
- Simplest scenario: just implement IEnumerable interface and let LINQ to Object take care of all the other LINQ operations.
- More complex: implement IQueryable interface and provide custom implementations of various query operations (select, from, where, …).
	- a complex IQueryable provider, such as the LINQ to SQL provider, might translate complete LINQ queries to an expressive query language, such as SQL.

![[Pasted image 20250412225232.png]]


### 6.12 Parallel LINQ (PLINQ)
Parallel LINQ (PLINQ) is a parallel implementation of LINQ to Objects.
- PLINQ implements the full set of LINQ standard query operators as extension methods for the System.Linq namespace and has additional operators for parallel operations.


![[Pasted image 20250412225313.png|500]]

### 6.13 Java Streams
![[Pasted image 20250412225350.png|500]]
