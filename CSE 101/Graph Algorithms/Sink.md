vertices in a graph that has no outgoing edges

the sink in a DAG can be found by reversing all the edges and finding the source, then the SCC that contains that source is the sink in the original graph.