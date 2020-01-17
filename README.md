# spark_pagerank
pyspark pagerank script

The idea for this short script stems from the problem that when you try to pagerank a large graph with spark and are using either the graphx library or the graphframes library  you will quickly run out of memory because those two create triplets over the whole graph which is a large number when your graph is already really large. So I implemented a pagerank algorithm that can:

- deals with edges that go to a node not found in the graph (edges that go to destinations that don't also appear as sources)
- deal with nodes that have no outward edges (dangling nodes)

the rank in each case is added to alpha and redistributed to the whole graph

# The graph is expected to look like this:

|src | dst|
|---|---|
| 1     | 1|
| 1     | 3|
| 3     | 4|
| 2     | 5|
| 6     | None|

dangling nodes are depicted as `source_id,None` meaning that source_id has no out edges

