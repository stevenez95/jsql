###Building a simple select
    Select select = SelectUtils.buildSelectFromTable(new Table("mytable"));

**select** contains now **select * from mytable**.

    Select select = SelectUtils.buildSelectFromTableAndExpressions(new Table("mytable"), new Column("a"), new Column("b"));

**select** contains now **select a, b from mytable**.

Or even simpler, if you do not want to build the right expression tree you can provide simple textual expressions, that will be parsed and included in your **select**.

    Select select = SelectUtils.buildSelectFromTableAndExpressions(new Table("mytable"), "a+b", "test");

###Extending a simple insert

```
Insert insert = (Insert)CCJSqlParserUtil.parse("insert into mytable (col1) values (1)");
System.out.println(insert.toString());

//adding a column
insert.getColumns().add(new Column("col2"));

//adding a value using a visitor
insert.getItemsList().accept(new ItemsListVisitor() {

    public void visit(SubSelect subSelect) {
	throw new UnsupportedOperationException("Not supported yet.");
    }

    public void visit(ExpressionList expressionList) {
	expressionList.getExpressions().add(new LongValue(5));
    }

    public void visit(MultiExpressionList multiExprList) {
	throw new UnsupportedOperationException("Not supported yet.");
    }
});
System.out.println(insert.toString());

//adding another column
insert.getColumns().add(new Column("col3"));

//adding another value (the easy way)
((ExpressionList)insert.getItemsList()).getExpressions().add(new LongValue(10));

System.out.println(insert.toString());
```
