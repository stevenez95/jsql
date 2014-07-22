Due to the lack of significant improvements of JavaCC over the last years, I got the impression one should think about a switch of the parser generator.

After playing around and testing a bit of ANLTR 4 I am quite impressed about the easieness to transform and improve JavaCCs JSQLParser grammar to ANTLR 4. Still there are some things to solve:

* keywords as identifier: solution would be like now
* deparsing has to be separated again since the tree node classes of ANTLR could not be provided, like in JavaCC but are automatically generated
* tooling around JSqlParser should be rebuild (e.g. TableNameExtractor)

I appreciate any comments to this.

Maybe there is another generator at hand that would be even better to use.
