# What is JSqlParser?
JSqlParser is a SQL statement parser. It translates SQLs in a traversable hierarchy of Java classes. JSqlParser is not limited to one database but provides support for a lot of specials of Oracle, SqlServer, MySQL, PostgreSQL ... To name some, it has support for Oracles join syntax using (+), PostgreSQLs cast syntax using ::, relational operators like != and so on. Then the result can be accessed in a structured way. 
The generated Java class hierarchy can be navigated using the [Visitor Pattern](http://en.wikipedia.org/wiki/Visitor_pattern).

# Contributions
To help JSqlParsers development you are encouraged to provide 
* feedback
* bugreports
* pull requests for new features
* improvement requests

Also I would like to know about needed examples or documentation stuff. 

#Donations

If you want to contribute or help this way, here is the possibility: [![Flattr](http://api.flattr.com/button/flattr-badge-large.png)](https://flattr.com/submit/auto?user_id=wumpz&url=http%3A%2F%2Fgithub.com%2FJSQLParser%2FJSqlParser) [![PayPal donate button](http://img.shields.io/paypal/donate.png?color=yellow)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=64CCN9JJANZXA "Help this JSqlParser version using Paypal")  

#Modifications
JSqlParser is continuously improved. All modifications could be followed at the
[Release Notes](https://github.com/JSQLParser/JSqlParser/releases). Additional News can be found [here](News).

Modifications before GitHubs release tagging are listed in the [Older Releases](Older Releases) page.

# How it works?
The parser is built using **JavaCC**. The core JavaCC grammar for SQL has been taken from Guido Draheim's site and has been changed in order to produce a hierarchy of Java classes. The classes called **deparsers** are used to build again the SQL text of the class hierarchy.

Over the time the grammar was extended and now is a combination of specialities of grammars of various database systems. It is grown by need. So some (not all) Oracle, MySql, SQLServer, PostgreSQL specific aspects can be parsed.

# Maven
To use **JSqlParser **in a maven project you have to include the following dependency:

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


## Original project

This is a fork of the jsqlparser originally developed by ultimoamore.

Original project websites:

* http://jsqlparser.sourceforge.net
* http://sourceforge.net/projects/jsqlparser/
