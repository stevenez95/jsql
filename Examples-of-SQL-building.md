###Building a simple select
    Select select = SelectUtils.buildSelectFromTable(new Table("mytable"));

**select** contains now **select * from mytable**.

    Select select = SelectUtils.buildSelectFromTableAndExpressions(new Table("mytable"), new Column("a"), new Column("b"));

**select** contains now **select a, b from mytable**.

Or even simpler, if you do not want to build the right expression tree you can provide simple textual expressions, that will be parsed and included in your **select**.

    Select select = SelectUtils.buildSelectFromTableAndExpressions(new Table("mytable"), "a+b", "test");

###Extending a simple insert

```java
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

###Replacing String values

Somebody wanted to publish some SQLs but wanted to scramble all concrete values. So here is a little example of how to achieve this. 
In short a visitor scans through the complete tree, finds all **StringValues** and replaces the 
current value with **XXXX**. Using the new Adaptorclasses of JSqlParser 0.9 this could be achieved without using the Deparser.

```java
String sql ="SELECT NAME, ADDRESS, COL1 FROM USER WHERE SSN IN ('11111111111111', '22222222222222');";
Select select = (Select) CCJSqlParserUtil.parse(sql);

//Start of value modification
StringBuilder buffer = new StringBuilder();
ExpressionDeParser expressionDeParser = new ExpressionDeParser() {

    @Override
    public void visit(StringValue stringValue) {
	this.getBuffer().append("XXXX");
    }
    
};
SelectDeParser deparser = new SelectDeParser(expressionDeParser,buffer );
expressionDeParser.setSelectVisitor(deparser);
expressionDeParser.setBuffer(buffer);
select.getSelectBody().accept(deparser);
//End of value modification


System.out.println(buffer.toString());
//Result is: SELECT NAME, ADDRESS, COL1 FROM USER WHERE SSN IN (XXXX, XXXX)
```