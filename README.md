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
This week objective was to choose a centrality measure to identify the most central node in the network. subsequently, we had to plot the cumulative distribution of these centrality values on a graph. 

### Closeness centrality 
The first part involved the choice of a centrality measure, and we decided for closeness centrality. In our graph, this metric appeared particularly pertinent as it provides insights into how proximate a node (representing a character in this context) is to all other nodes in the network. This proximity indicates the centrality of these characters in the unfolding narrative. Such characters are presumed to play crucial roles as they are intricately connected to multiple storylines or engaged with various groups of characters, thereby emerging as pivotal figures in the storyline.
The function iterates through each node to compute the shortest path lengths from that node to all the others, considering edge weights if specified. The closeness centrality for each node is then determined as the reciprocal of the sum of all these shortest path lengths, multiplied by the total number of nodes minus 1 (N-1).

### cumulative distribution function 
In the second part of this week we had to implement a function to plot the cumulative distribution of closeness centrality. the function is created by dividing the range of sorted valued by the total number of values. The code then loads the graph and visualizes it, highlighting the top 5 characters with the highest closeness centrality, showcasing them in red on the graph. 

## Week 5: PageRank function
## Objective
This week objective is to write a function to compute the PageRank of the nodes in the graph and identify the node with the highest value. Moreover, we need to compare it with the one we got in Week 3 and draw our conclusions,as well as provide the cumulative distribution and again comparing it with the one we got in Week 3, commenting all the results obtained. 

## PageRank function
First of all, with *load_graph* function we read nodes and edges from CSV files and constructed a directed graph. Then, we implemented a *PageRank function* that we called *calculate_pagerank*: it initializes the PageRank scores at 1/number of nodes, this means that at the beginning each node is considered equally important.  After that the function iteratively updates them using the function (scriviamola non so come si fa). At each iteration, it checks if the PageRank values have converged, and this is done by calculating the sum of absolute differences between the new and old PageRank scores. If it is less than 1×10^−6, it considers the algorithm to have converged. Finally,  the function returns the PageRank values and the number of iterations it took to converge. If the PageRank doesn't converge within the specified number of iterations, it will return the values at the last iteration.The PageRank values that are returned represent the relative "importance" or "authority" of each node within the network. Nodes with higher PageRank values are considered to be more important or to have more influence within the network.

## Function to plot the cumulative distribution
In the second part of this week, we had to provide a cumulative distribution and compare it with the one we got in Week 3. In order to achieve this, the function *plot_cumulative_distribution* takes a dictionary of centrality values (in this context, PageRank values) and a title string as its arguments. This function is designed to visualize how the PageRank values are distributed across all the nodes in the network. It sorts the centrality values in ascending order and then computes the cumulative distribution, which is a way to show the percentage of nodes that have a PageRank value less than or equal to a certain threshold, used to understand the spread of centrality across the nodes in the graph. This helps us understand what fraction of nodes have low importance versus high importance according to PageRank. A plot is created using matplotlib that shows how many nodes have a PageRank value less than or equal to each value on the x-axis.
This type of plot is useful for visualizing the distribution of PageRank values across the graph, showing whether they are concentrated among a few nodes or more evenly distributed.
Afterwards, we computed the PageRank using the function *calculate_pagerank* using the graph G as argument. The *plot_cumulative_distribution* function is called with the PageRank values and the title 'PageRank' to create and display the cumulative distribution plot.
This algorithm allows us to visualize and understand the importance of nodes within a network, such as who are the most influential or well-connected individuals in a social network. The visualizations make it easier to interpret the data and can provide insights into the structure and dynamics of the network.
