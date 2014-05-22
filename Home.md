# What is JSqlParser?
JSqlParser parses an SQL statement and translate it into a hierarchy of Java classes.
The generated hierarchy can be navigated using the [Visitor Pattern](http://en.wikipedia.org/wiki/Visitor_pattern).

#Modifications
This fork is continuusly improved. All modifications could be followed at the
[Release Notes](https://github.com/JSQLParser/JSqlParser/releases).

# How it works?
The parser is built using JavaCC. The core JavaCC grammar for SQL has been taken from Guido Draheim's site and has been changed in order to produce a hierarchy of Java classes. 

# SourceCode and Tools
Visit JSqlParsers Sonar place [here](wiki/Sonar-scan-results) (thanks to vasilievip)

# Maven
To use JSqlParser in a maven project you have to include the following dependency:

```
<dependency>
    <groupId>com.github.jsqlparser</groupId>
    <artifactId>jsqlparser</artifactId>
    <version>0.9</version>
</dependency>
```


# Examples
Find some examples of JSqlParsers usage.
* Parsing [here](wiki/Examples-of-SQL-parsing). 
* Building [here](wiki/Examples-of-SQL-building).

* Simple expression evaluation [here](wiki/Example-of-expression-evaluation)

Feel free to provide more examples. 