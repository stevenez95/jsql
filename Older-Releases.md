These are the modifications done before githubs relase tagging.

## Extensions Version 0.8.3

* Added support for cross join 
* Allowed complex expressions in extract from
* Corrected cast expression to make type parameters usable (e.g. cast(col1 as varchar(255))
* Added support for column comma list in partition by statements
* Added support for columns names in create view statements

```sql
create view testView (col1,col2) as select a, b from table
```
* Added support for column cast using ::
* Added support for from clause in update statements

```sql
update tab1 set c=5 from tab1 inner join tab2 on tab1.col1=tab2.col2
``` 
* Corrected TableNamesFinder to work with update statements additions.
* Added support for simple create materialized view statements without additional parameters.

```sql
create materialized view testView as select a, b from table
```
* Added support for simple create index statements

```sql
create index myindex on mytab (mycol, mycol2)
```

## Extensions til Version 0.8.2

* Changed project tests to junit 4
* Changed project layout to maven project
* Added regexp (REGEXP) operator
* Added support for SELECT without FROM  (e.g. "SELECT 1+2")
* Moved parser from using StringBuffer to using StringBuilder
* Added support for CAST expression

```sql
select cast(col as varchar) from table
```
* Added support for modulo (a % b)
* Added support for brackets quotation
* Added support for NOT expr IS (expr IS NOT was already supported)
* Added support for Oracles (+) Join Syntax

```sql
select * from taba, tabb where taba.a=tabb.a(+)
```
* Added alias visitor to add aliases to selections
* Added connect visitor
* TableNamesFinder moved from tests to main source
* Added proper support for sets (union, intersect)

```sql
select a from taba union select b from tabb
select a from taba intersect select b from tabb
select a from taba except select b from tabb
select a from taba minus select b from tabb
```
* Added support for `extract(year from datetime-expr)`
* Start implementation of analytical expressions
* merged support for CREATE VIEW 
* Added lateral subquery support
* Added support for multi values insert statement

```sql
insert taba (col1,col2) values (1,2), (2,5), (3,20)
```
* Added support for multi values in select statement

```sql
SELECT col FROM (VALUES 1,2) AS MY_TABLE(col)
```
* Added extended support for analytic expressions (empty over clause, parameter within aggregat function)

```sql
SELECT sum(a) over () FROM taba
```