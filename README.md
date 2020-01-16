# spark_pagerank
pyspark pagerank script

The idea for this short script stems from the problem that when you try to pagerank a larg graph with spark and are using either the graphx libary or the graphframes libary (which is a python wraper for graphx) you will quickly run out of memory because those two create tripplets over the whole graph which is a large number when your graph is already really large. So I implemented a pagerank algorythem that can:

- deal with edges that go to a node not found in the graph 
- to a node that is unkown
- deal with nodes that have no outward edges (dangling nodes)

the rank in each case is added to alpha and redistributed to the whole graph

# Graphes are expected to look like this:

```
origin | destination
-------+------------
 1     | 1
 1     | 3
 3     | 4
 2     | 5
 4     | None
```