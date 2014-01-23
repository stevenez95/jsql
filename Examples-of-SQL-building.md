###Building a simple select
    Select select = SelectUtils.buildSelectFromTable(new Table("mytable"));

**select** contains now **select * from mytable**.

    Select select = SelectUtils.buildSelectFromTableAndExpressions(new Table("mytable"), new Column("a"), new Column("b"));

**select** contains now **select a, b from mytable**.

Or even simpler, if you do not want to build the right expression tree you can provide simple textual expressions, that will be parsed and included in your **select**.

    Select select = SelectUtils.buildSelectFromTableAndExpressions(new Table("mytable"), "a+b", "test");
