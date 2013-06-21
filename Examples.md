### Simple SQL parsing
    Statement stmt = CCJSqlParserUtil.parse("SELECT * FROM tab1");

Starting from **stmt** you can dive into the parsing result. 

### Extract table names from SQL
    Statement statement = CCJSqlParserUtil.parse("SELECT * FROM MY_TABLE1");
    Select selectStatement = (Select) statement;
    TablesNamesFinder tablesNamesFinder = new TablesNamesFinder();
    List<String> tableList = tablesNamesFinder.getTableList(selectStatement);

In **tableList** are all table names of the parsed SQL statement. The table names finder is an example of JSqlParser visitor pattern structure. You can use the visitor pattern to traverse the parsing result and compute on it.