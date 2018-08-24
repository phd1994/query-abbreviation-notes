### How long does it take to run testAbridgementLogic?

testAbridgementLogic() method tests the invariants in abbreviation process on the queries added to `queries` list. 

The following plot describes the histogram of time taken by different queries to go through testAbridgementLogic(string) method.


(1) Excluding SQL_PARSER.createStatement() call

![plot 1](https://github.com/phd1994/query-abbreviation-notes/blob/master/images/testTimeExCreateStatement.png "Test execution time excluding createStatement() call")

(2) Including SQL_Parser.createStatement() call

![plot 2](https://github.com/phd1994/query-abbreviation-notes/blob/master/images/testTimeIncCreateStatement.png "Test execution time including createStatement() call")

