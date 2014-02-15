# What is JSqlParser?
JSqlParser parses an SQL statement and translate it into a hierarchy of Java classes.
The generated hierarchy can be navigated using the [Visitor Pattern](http://en.wikipedia.org/wiki/Visitor_pattern).

# How it works?
The parser is built using JavaCC. The core JavaCC grammar for SQL has been taken from Guido Draheim's site and has been changed in order to produce a hierarchy of Java classes. 

# SourceCode and Tools
Visit JSqlParsers Sonar place [here](wiki/Sonar-scan-results) (thanks to vasilievip)

# Examples
Find some examples of JSqlParsers usage.
* Parsing [here](wiki/Examples-of-SQL-parsing). 
* Building [here](wiki/Examples-of-SQL-building).

* Simple expression evaluation [here](wiki/Example-of-expression-evaluation)

Feel free to provide more examples. 