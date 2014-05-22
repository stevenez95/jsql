# What is JSqlParser?
JSqlParser parses an SQL statement. Then the result can be accessed in a structured way. 
The generated Java class hierarchy can be navigated using the [Visitor Pattern](http://en.wikipedia.org/wiki/Visitor_pattern).

#Modifications
JSqlParser is continuously improved. All modifications could be followed at the
[Release Notes](https://github.com/JSQLParser/JSqlParser/releases). Additional News can be found [here](News).

Modifications before GitHubs release tagging are listed in the [Older Releases](Older Releases) page.

# How it works?
The parser is built using JavaCC. The core JavaCC grammar for SQL has been taken from Guido Draheim's site and has been changed in order to produce a hierarchy of Java classes. 

Over the time the grammar was extended and now is a combination of specialities of grammars of various database systems. So some (not all) Oracle, MySql, SQLServer, PostgreSQL specific aspects can be parsed.

# Maven
To use JSqlParser in a maven project you have to include the following dependency:

```
<dependency>
    <groupId>com.github.jsqlparser</groupId>
    <artifactId>jsqlparser</artifactId>
    <version>0.9</version>
</dependency>
```
Be sure you added the latest release.

# Examples
Find some examples of JSqlParsers usage.
* Parsing [here](wiki/Examples-of-SQL-parsing). 
* Building [here](wiki/Examples-of-SQL-building).

* Simple expression evaluation [here](wiki/Example-of-expression-evaluation)

Feel free to provide more examples. 