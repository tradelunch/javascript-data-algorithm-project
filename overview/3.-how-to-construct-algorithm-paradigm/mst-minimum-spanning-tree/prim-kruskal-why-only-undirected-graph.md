# Prim, Kruskal Why? only undirected graph?

{% embed url="https://www.baeldung.com/cs/prims-kruskals-on-directed-graph" %}





In our example, there is just one MSA possible. That is ![s \rightarrow b \rightarrow a](https://www.baeldung.com/wp-content/ql-cache/quicklatex.com-d6bd0d85ea16310aecdc6093e51b0e14\_l3.svg). But running Kruskal’s algorithm, we first of all select ![a \rightarrow b](https://www.baeldung.com/wp-content/ql-cache/quicklatex.com-ee198936a9dcafc919babfb3a66d5f74\_l3.svg):

&#x20;

![g4](https://www.baeldung.com/wp-content/uploads/sites/4/2021/12/g4-300x296.png)

**Since this edge is not contained in our MSA it is impossible to construct one from the Kruskal algorithm in this example.**

#### 3.2. Prim <a href="#bd-2-prim" id="bd-2-prim"></a>

For the Prim algorithm, we have a similar setup:

&#x20;

![g5](https://www.baeldung.com/wp-content/uploads/sites/4/2021/12/g5-240x300.png)

This time the only possible MSA is ![s \rightarrow a \rightarrow b](https://www.baeldung.com/wp-content/ql-cache/quicklatex.com-b6177c09e0777c18db652a303d3b2035\_l3.svg). Prim’s algorithm starts at a random node, in this case, ![s](https://www.baeldung.com/wp-content/ql-cache/quicklatex.com-1edc883862ceed1a21913f60358e31d8\_l3.svg). It then takes the edge with the lowest edge connected to ![s](https://www.baeldung.com/wp-content/ql-cache/quicklatex.com-1edc883862ceed1a21913f60358e31d8\_l3.svg), which is the node to ![b](https://www.baeldung.com/wp-content/ql-cache/quicklatex.com-ad69adf868bc701e561aa555db995f1f\_l3.svg):

&#x20;

![g6](https://www.baeldung.com/wp-content/uploads/sites/4/2021/12/g6-240x300.png)

**Since the edge,** ![s \rightarrow b](https://www.baeldung.com/wp-content/ql-cache/quicklatex.com-26fbc302547dc11b32403243061231fc\_l3.svg) **is not contained in the only MSA that the following steps won’t generate an MSA for this example.**
