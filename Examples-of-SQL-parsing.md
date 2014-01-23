### Simple SQL parsing
    Statement stmt = CCJSqlParserUtil.parse("SELECT * FROM tab1");

Starting from **stmt** you can dive into the parsing result. 

### Simple Expression parsing
    Expression expr = CCJSqlParserUtil.parseExpression("a*(5+mycolumn)");

Starting from **expr** you can use the parsing result.

### Extract table names from SQL
    Statement statement = CCJSqlParserUtil.parse("SELECT * FROM MY_TABLE1");
    Select selectStatement = (Select) statement;
    TablesNamesFinder tablesNamesFinder = new TablesNamesFinder();
    List<String> tableList = tablesNamesFinder.getTableList(selectStatement);

In **tableList** are all table names of the parsed SQL statement. The table names finder is an example of JSqlParser visitor pattern structure. You can use the visitor pattern to traverse the parsing result and compute on it.

### Apply aliases to all expressions
    Select select = (Select) CCJSqlParserUtil.parse("select a,b,c from test");
    final AddAliasesVisitor instance = new AddAliasesVisitor();
    select.getSelectBody().accept(instance);

As a result you will get **SELECT a AS A1, b AS A2, c AS A3 FROM test**. At the moment the prefix
can be configured.

### Add a column or expression to a select
    Select select = (Select) CCJSqlParserUtil.parse("select a from mytable");
    SelectUtils.addExpression(select, new Column("b"));

Now **select** contains **SELECT a, b FROM mytable**.