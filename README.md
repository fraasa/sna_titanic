# Social Network Analysis (SNA) Project: Exploring the Titanic Dataset

## Project Overview

### group member
the minds behind this social network analysis journey in the Titanic's network are: Leonardo Azzi, Sofia Bruni, Francesca Romana Sanna, Alexandra Tabarani, and Marta Torella.

Welcome to the repository of our Social Network Analysis (SNA) project, where we delve into exploring the intricate web of relationships and interactions among characters from the Titanic dataset. Throughout the course weeks, we aim to not only visually represent these connections but also analyze them through various graph metrics.

*Title: Unveiling Titanic's Social Fabric: A Network Analysis*

*Introduction:*

In our Social Network Analysis (SNA) project, the characters aboard the Titanic take center stage as nodes, while the edges connecting them represent shared scenes, their weights reflecting the frequency of these shared appearances. This analytical approach allows us to decode the complex web of interactions that shaped the destinies of the movie characters.

Through meticulous examination, we aim to uncover not only the characters but also the subtle patterns of connection that underscore the narrative. Moreover, our goal is to enrich our network with previously undiscovered information.

Join us as we navigate the network to understand the Titanic's social dynamics!

## Week 1: Introduction to Graph Creation and Basic Analysis

### Objective
The primary objective this week was to construct a visual representation of a graph, representing the relationships and interactions among the characters in the Titanic dataset.

### Graph Construction
In our graphical representation:
- **Nodes**: Represent individual characters from the dataset.
- **Edges**: Indicate relationships between characters, where the thickness of an edge signifies the frequency of scenes shared by the connected characters.

### Graph Analysis
We further analyzed the graph by determining some fundamental properties:
- **Total Number of Nodes and Edges**: To understand the scale and complexity of the graph.
- **Average Degree**: Computed using the formula \(\frac{2E}{N}\), where \(E\) represents the total number of edges and \(N\) is the number of nodes in the graph. This metric gives an average indication of the number of connections per node.
- **Graph Density**: Calculated using the formula \(D = \frac{2E}{N \times (N-1)}\), where \(D\) represents the graph density, \(E\) is the total number of edges, and \(N\) is the number of nodes. This metric provides insights into the overall connectivity of the graph.

### Insights Gained
By calculating these metrics, we were able to deepen our understanding of the relationships and interactions among the characters in our dataset, providing a foundational knowledge that will be expanded upon in the subsequent weeks.

## Week 2: Average Clustering and Transitivity number

### Objective
This week objective was to exploit some centrality measures (Average Clustering and Transitivity) in order to better analyze the network's structural characteristics by identifying the key nodes. 

### Average Clustering and Transitivity number with Networkx
As a first step we implemented the Average Clustering and the Transitivity by using the respective built-in functions in Networkx; both metrics were used to understand the interconnectedness among nodes in our network.
-**Average Clustering**: the average of the clustering coefficients. Each clustering coefficient is computed as the ratio of the number of triangles in which the node we are considering (let's say node i) participates, over the number of wedges of that same node (computed as [ki(ki-1/2)], where ki is the degree of node i ). 
-**Transitivity**: defined as the ratio between the total number of triangles in the network, over the number of wedges divided by three. The mathematical formula related to transitivity could also be expressed as the number of triangles multiplied by three over the sum of all clustering coefficients.

### Compute_Transitivity Implementation
In the second part of this week task, we had to implement from scratch our transitivity function. Our function starts by manually counting the number of triangles in the network by iterating over each node in the graph; by doing so, it finds the neighbours of each node and registers the common ones between one node and its neighbors (which indicates the number of triangles involving the current node). Then the 'triangles' variable, in which the number of triangles in the graph were stored, is divided by 6, since each triangle was originally counted six times( two times for each node of the traingles). Once we obtained the total number of triangles, we start looking for the wedges (or connected triplets) by iterating again through each node in the graph in order to identify again its neighbours and degree so that we could apply the mathematical formula for the number of wedges [ki(ki-1/2)]. The final step of our code computes the Transitivity number as the  number of triangles multiplied by three over the sum of all number of wedges.

## Week 3: Closenness Centrality

### Objective
this week objective was to choose a centrality measure to identify the most central node in the network. subsequently, we had to plot the cumulative distribution of these centrality values on a graph. 

### Closeness centrality 
the first part involved the choice of a centrality measure, and we decided for closeness centrality. In our graph, this metric appeared particularly pertinent as it provides insights into how proximate a node (representing a character in this context) is to all other nodes in the network. This proximity indicates the centrality of these characters in the unfolding narrative. Such characters are presumed to play crucial roles as they are intricately connected to multiple storylines or engage with various groups of characters, thereby emerging as pivotal figures in the storyline.
the function iterates through each node to compute the shortest path lengths from that node to all the others, considering edge weights if specified. the closeness centrality for each node is then determined as the reciprocal of the sum of all these shortest path lengths, multiplied by the total number of nodes minus 1 (N-1).

### cumulative distribution function 
in the second part of this week we had to implement a function to plot the cumulative distribution of closeness centrality. the function is created by dividing the range of sorted valued by the total number of values. the code then loads the graph and visualizes it, highlighting the top 5 character with the highest closeness centrality, showcasing them in red on the graph. 

