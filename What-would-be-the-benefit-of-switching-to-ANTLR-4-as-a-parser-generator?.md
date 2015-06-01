Due to the lack of significant improvements of JavaCC over the last years, I got the impression one should think about a switch of the parser generator.

After playing around and testing a bit of ANLTR 4 I am quite impressed about the easieness to transform and improve JavaCCs JSQLParser grammar to ANTLR 4. Still there are some things to solve:

* keywords as identifier: solution would be like now
* deparsing has to be separated again since the tree node classes of ANTLR could not be provided, like in JavaCC but are automatically generated
* tooling around JSqlParser should be rebuild (e.g. TableNameExtractor)

But there are significant improvements automatically at hand. 

* ANTRL 4 generates listener and visitors for the parse tree. 
* semantic predicates to disable rules
* the grammar is much easiear to read
* automatic operator precedence


I appreciate any comments to this.

Maybe there is another generator at hand that would be even better to use.


**Update:**
After playing around with **JJTree** a bit, I noticed that most of my *significant improvements* of ANTLR 4 are already there. 

* listener and visitor patterns are generated on demand
* the readability of the grammar is no point, because I did not compare a cleaned up JavaCC grammar with the clean ANTLR 4 grammar, using ANTLR 4 I would also like to have some container objects (e.g. **Select**) created

* semantic predicates to disable rules are not available but not needed at the moment, lexical states are there

Therefore the a significant improvement would be *automatic operator precedence*, which would result in a smaller grammar.
