## How long does it take to run QueryAbridger::abridge?

The following table shows a comparison between the execution times of `SQL_PARSER::createStatement` and `QueryAbridger::abridge`. Threshold used is `10000 characters`.

The query used for this experiment looks like the following:

`select foobar from barfoo where foofoo not in ('abc', 'abc', ..... 'abc')`. 

Every row represents the same query with different repeatition counts for 'abc' string inside the `IN` clause. The number of `abc` string literals roughly translates to number of nodes in the tree. 

Number of Nodes | Time taken by SQL_PARSER::createStatement() | Time taken by QueryAbridger::abridge |
------------ | ------------- | -------------
~5000 | 70.22ms | 37.83ms
~10000 | 80.16ms | 42.50ms
~50000 | 435.38ms | 236.89ms
~100000 | 307.31ms | 185.43ms
~500000 | 3500.15ms | 784.28ms

(The long queries we have observed are between 10000 and 50000 nodes.) 

## How long does it take to run testAbridgementLogic?

testAbridgementLogic() method tests the invariants in abbreviation process on the queries added to `queries` list. 

The following plot describes the histogram of time taken by different queries to go through testAbridgementLogic(string) method.


(1) Excluding SQL_PARSER.createStatement() call

![plot 1](https://github.com/phd1994/query-abbreviation-notes/blob/master/images/testTimeExCreateStatement.png "Test execution time excluding createStatement() call")

(2) Including SQL_Parser.createStatement() call

![plot 2](https://github.com/phd1994/query-abbreviation-notes/blob/master/images/testTimeIncCreateStatement.png "Test execution time including createStatement() call")

