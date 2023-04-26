# database normalization form and acid

## acid

- **A** `atomicity`

      > Transactions are often composed of multiple statements.
      > Atomicity guarantees that each transaction is treated as a single "unit",
      > which either succeeds completely or fails completely:
      > if any of the statements constituting a transaction fails to complete,
      > the entire transaction fails and the database is left unchanged.

- **C** `consistency`

   > Consistency ensures that transaction can only bring the database
   >   from one consistent state to another, preserving database invariants:
   >   any data written to the database must be valid according to all defined rules,
   >  including constraints, cascades, triggers, and any combination thereof.

- **I** `isolation`

      > Transactions are often executed concurrently
      > (e.g., multiple transactions reading and writing to a table at the same time).
      > Isolation ensures that concurrent execution of transactions leaves the database
      > in the same state that would have been obtained if the transactions were executed sequentially.

- **D** `durability`

      > Durability guarantees that once a transaction has been committed,
      > it will remain committed even in the case of system failure
      > (e.g., power outage or crash). This usually means that completed transactions
      > (or their effects) are recorded in non-volatile memory.

## normalization forms

`first normal form `

> - eliminate repeating groups in individual tables.
> - create a separate table for each set of related data.
> - identify each set of related data with a primary key.

`second normal form`

> - create separate tables for sets of values that apply to multiple records.
> - relate these tables with a foreign key.

`third normal form`

> - eliminate fields that do not depend on the key

### resources

- [acid](https://en.wikipedia.org/wiki/ACID)
- [db normalization](https://learn.microsoft.com/en-us/office/troubleshoot/access/database-normalization-description)
