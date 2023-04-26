# sql

- `create db`

  ```sql
   CREATE database testDB;
  ```

- `create table`

```sql
CREATE TABLE Persons (
    PersonID int,
    LastName varchar(255),
    FirstName varchar(255),
    Address varchar(255),
    City varchar(255)
);
```

- `delete column`

```sql
DELETE FROM Customers;
```

- `insert data`

```sql
INSERT INTO Customers (CustomerName, ContactName, Address, City, PostalCode, Country)
VALUES ('Cardinal', 'Tom B. Erichsen', 'Skagen 21', 'Stavanger', '4006', 'Norway');
```

- `join`

```sql
SELECT Orders.OrderID, Customers.CustomerNameFROM OrdersINNER JOIN
  Customers ON Orders.CustomerID = Customers.CustomerID;
```

- `select`

```sql
SELECT CustomerName, City FROM Customers;
```

- `where`

```sql
SELECT * FROM Customers
WHERE Country='Mexico';
```

### resource

- [sql reference](https://www.w3schools.com/sql/sql_ref_keywords.asp)
