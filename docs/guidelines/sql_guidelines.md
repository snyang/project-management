# SQL Guidelines

## SQL Style

### style types

| type        | examples    |
| ----------- | ----------- |
| lower case  | lower_case  |
| upper case  | UPPER_CASE  |
| pascal case | PascalCase  |
| camel case  | camelCase   |
| pascal_case | Pascal_Case |
| camel_case  | camel_Case  |

### file name styles

| type           | style                      | examples             |
| -------------- | -------------------------- | -------------------- |
| package header | pkg_<PascalCase>.sql       | pkg_UserManager.sql  |
| package body   | pkb_<PascalCase>.sql       | pkb_UserManager.sql  |
| trigger        | trg_<TableName>_<Type>.sql | trg_User_InsertA.sql |
| function       | fun_<PascalName>.sql       | fun_StringUtil.sql   |
| default        | <PascalCase>.sql           | CreateTables.sql     |

### name styles

| item          | style       | examples     |
| ------------- | ----------- | ------------ |
| keywords      | lower case  | select       |
| table name    | pascal case | Department   |
| table alias   | lower case  | d            |
| field name    | pascal case | DepartmentId |
| field alias   | pascal case | FullName     |
| package name  | pascal case | UserManager  |
| function name | camel case  | findUser     |

### statements styles

> main idea:
> keep things align

- For SELECT statements, the align position is 8.
- For nested SELECT statements, the align position is the above indent position + 8.
- For nested condition statements (conditions in a pair of brackets), the align position is the above indent position + 4.

- If the align position is N,
  - For keywords which has N - 1 characters or or less than N -1 characters, right align at the position N - 1.
  - For above case, the follow is in the same line of its keyword at the position N + 1.
  - For keywords which has N characters or more than N characters:
    - Option 1.1:
        - Keep the keyword in an isolated line.
        - For above case, the follow is in the next line at the position N + 1.
    - Option 1.2:
        - Keep the keyword with the follow are in the same line.
- For comma, put it at the begin of line with a space at the position of N - 1.

- For nested statements, keep the left bracket at end of the line
- For nested statements:
    - Option 2.1: keep the right bracket in an isolated line
    - Option 2.2: keep the right bracket with the follow are in same line

- Put simple things first

- Sample: Keywords in lowercase

```SQL
 select d.DepartmentId
      , d.DepartmentName
      , e.EmployeeName
      , case
           when e.Gender = 1
           then 'F'
           else 'M'
        end
        as GenderName
      , (
         select n.full_Name
           from Names n
          where n.Name_Id = d.EmployeeId
        ) -- option 2.1
        as FullName
   from Departments d
inner join -- option 1.1
        Employees e
     on e.DepartmentId = d.DepartmentId
    and (
            e.enabled = 1
         or e.status = 'super'
        )
inner join -- option 1.1
       (
         select EmployeeId
           from Employees
          where EmployeeName = 'Joe'
        ) Managers m -- option 2.2
     on m.EmployeeId = e.ManagerId
  where d.type = 1
    and d.status = 'active'
order by d.DepartmentName  -- option 1.2
      , e.EmployeeName
```

- Sample: Keywords in uppercase

```SQL
 SELECT d.DepartmentId
      , d.DepartmentName
      , e.EmployeeName
      , (
         SELECT n.full_Name
           FROM Names n
          WHERE n.Name_Id = d.EmployeeId
        ) -- option 2.1
        AS FullName
   FROM Departments d
INNER JOIN Employees e -- option 1.2
     ON e.DepartmentId = d.DepartmentId
    AND (
            e.enabled = 1
         OR e.status = 'super'
        )
INNER JOIN -- option 1.1
       (
         SELECT EmployeeId
           FROM Employees
          WHERE EmployeeName = 'Joe'
        ) Managers m -- option 2.2
     ON m.EmployeeId = e.ManagerId
  WHERE d.type = 1
    AND d.status = 'active'
ORDER BY d.DepartmentName
      , e.EmployeeName
```