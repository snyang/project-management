# Database Design Guidelines

## Principles
* Support popular databases

## Name Style
* Table Name
Style: Pascal
Example: Employee
It is fine that you may use the singular style or plural style. But singular style is preferred here.

* Column Name
Style: Pascal
Example: HouseAddress
Avoid to repeat table name in the column name, for example, For table 'Employee', use 'Name' for the column of employee name.

* Primary Key Name
Style: Pascal, PK_${TableName}  
Example: PK_Employee  

* Index Name  
Style: Pascal, UK_${Column1Name}_${Column2Name} for unique indexes.
Use IK_${Column1Name}_${Column2Name} for non-unique indexes.
Example: UK_Code

* Foreign Key Name  
Style: Pascal, FK_${Column1Name}_${Column2Name}  
Example: FK_DepartmentId

## Columns
### Text columns
* Do use unicode data type to define text columns.
* Do use n**var**char for variable length text columns.

### Date/Date Time
* If the value of a date column is expected to present same text result among different time zone, use numeric or text data type to define date/date-time columns.
If we define a column with date data type, default, most program language will use date-time type to store values from the column, we should realize the date value will be changed when the data is transited to a different time-zone. For example:
2001/01/15, On the database server, timezone is +8.
2001/01/15, On the application server, timezone is +8.
2001/01/15 01:00:00, On the client, timezone is +9.
So if it is a problem to you, try to use a integer or text data type to store the value.
> Tips: consider the case carefully. ask these questions:  
> If your application will be used in different time-zone?  
> If you only use date part for the column?
> If you only use time part for the column?

### Nullable
* Avoid to define a column as **nullable**.  
Avoid to use null would reduce programing bugs, and bring better performance.

* Do Not use null for numeric columns if it has same meaning as zero.
* Do Not use null for text columns if it has same meaning as empty.
* May use null in a reference column provide that null is acceptable.

## Keys
### Primary Keys
* Do create a primary key for any tables.
* Recommend to use one column for the primary key.
* Use '${TableName}Id' for the name of the primary key column, the column is denoted as 'Id' columns.
* Recommend to use integer data type for the primary key column.
* Avoid change the value of the primary key column after created.
* It is acceptable to show the the value of the primary key column to customers if need.

### Foreign Keys
* Do create a foreign key if there is a relation between 2 tables.
It is useful to keep data integrity.
* Carefully to use delete cascade clause when creating the foreign keys relationship.
> Tips: Be careful, using delete cascade is also dangerous. consider it twice before use it.

## Database-specific constraints
* Avoid to use reversed words for name of objects of databases
> Tips: please read the reversed words from database you will use
* Avoid to use system prefix in your object names
* Check length limitation of object names of databases

## Tables
### Entity Tables
Like departments, employee etc, we store these kind of information into entity tables.
In most case, the table like:
* Definition sample  

```sql
Employee {EmployeeId, Code, Name, DepartmentId, ...}.
```

If in your system, an employee only exists in one department, you may use above definition.

### Tree Tables
Like most organization, departments will be constructed as a tree, there are some top level departments (or is a root department), except these top level departments, departments **must have one and only have** one parent department.
We define this kind of table as:
* Definition sample  

```sql
Department{DepartmentId, Code, Name, **ParentId**, ...}.
```

In most case, for the usage convenience, we will define a tree table for each tree relationship, denoted as a tree table.
* Definition sample  
DepartmentTree{ParentId, ChildId}.
For a parent department, The table stores itself and all its descendants.
From a view of a child department, the table stores itself and all its ancestors.

### Hierarchical Tables
Different as tree tables, in the hierarchical tables, a child would have 0 to n parents.
For example, groups and users:
* Rules  
    * an user would exists in multiple groups.
    * an groups would exists in multiple groups.

* Definition sample  

```sql
User(userId, Name, isGroup)
GroupUser(parentId, userId)
GroupUserTree(parentId, userId)
```

The table **GroupUser** stores the direct relationships.
Instead, the table **GroupUserTRee** stores the redundant relationships like tree tables above.