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

## Week 6: 

## Week 7: Link Prediction
## Objective
This week oblective is to calculate different **topological similarity indices**, returning a frame where **each row**  is a **missing link** and **each column** is an **index**. Once similarity indices are computed, we have to **synthesize them properly** to obtain the **link likelihood scores**. We have to **calculate a score**, using an **aggregation function**, the **arithmetic mean** between the **two indices**, as another parameter of evaluation. This **value** obtained will be **added** through a third **column** in teh pandaframe. For **each of the 3 scores**, we will **identify** as **missing links** the **node pairs** yielding the **largest 5 values**. the **top 5 ones** are **identified as the predicted links**.

## *Transformation of the graph: undirected and unweighted without self loops*
We, first of all, **loaded both nodes and edges**, beside the graph, and we used a function to **convert** the **directed graph 'G'** to an **undirected graph 'U'**. Then, we used a function which **removes edges** that **connect a node to itself** (self-loops) from the undirected graph U. 
Moeover, we have **analyzed** the **Largest Connected Component** (LCC): firstly, we found it. Then we **created** a **subgraph LCC** containing **only the nodes** in the **largest connected component**, printing them. 

## Understanding the code
This type of function, is used specifically for **examining the structure and connections** within a graph represented by nodes and edges,  it's particularly focused on how nodes (characters) are interconnected through edges (relationships) in a network. The **focus** is on the **largest connected component** of the graph, which can be **critical** in **understanding the cohesion or segmentation** of the network.

## *Calculating the topologiacal indices*
We start by creating an **empty undirected graph** called **'G'**, loading then **all edges and nodes**. Therefore, we have **computed** two network **topological indices**, **Common Neighbors** (CN) and **Preferential Attachment** (PA), for **all non-existing edges** (potential future links) in a the graph, let's get in detail. After **identifying Non-Edges**, meaning all **pairs of nodes** in the graph that are **not connected by an edge**, we have calculated **CN**: for **each pair of non-connected nodes**, we calculated the **number of common neighbors** they share. This is a **measure of how many mutual connections two nodes have**, which can be extremely **important** to **indicate** the **likelihood of them forming** a possible **connection in the future**.
Afterwards, we calculated **PA**: for **each pair of non-connected nodes**, we obtained the **product** of their **degrees** (meaning the **number of connections** they have). This index is **based on the idea** that **nodes with higher degrees** are **more likely to form new connections**.
Fianlly, we created the **DataFrame** in order to **organize** the **CN and PA values** into a pandas DataFrame for **easier analysis and visualization**.

## Understanding the code
### Insights and Interpretations
- *Focusing on LCC*: Analyzing the largest connected component can be particularly insightful, as it represents the most interconnected part of the network, often containing crucial information about the network's structure.

- *Common Neighbors (CN)*: High CN values suggest that two nodes are part of tightly-knit communities, increasing the likelihood of a future link.

- *Preferential Attachment (PA)*: This concept, often related to the "rich-get-richer" phenomenon, suggests that nodes with many connections are more likely to acquire even more connections.

- *Predictive Analysis*: Both CN and PA are used in predicting the formation of future links in a network, which is a significant aspect of social network analysis, recommendation systems, and understanding network dynamics.

## *Computing the likelihood score: arithmetic mean*
The **rescal function** has the **purpose to rescale** a **pandas Series** to a **range of 0 to 1**, while the **min and max** functions help us to **identify** those values in the **series** and **returns the rescaled series** where **each value is transformed** to **fall within the range [0, 1]**. This is **done by subtracting** the **minimum value from each element** and **dividing** by the **range (max - min)**. 
After that, our **goal** is to **add** a **new column** with the **mean** for each **index**. We applied the **rescale function** to the **'CN' and 'PA'** columns in the DataFrame, **creating two new columns**: 'CN_scaled' and 'PA_scaled'. Finally, the **mean of the scaled values** ('CN_scaled' and 'PA_scaled') for each row is **calculated and added** this as a **new column 'Mean_CN_PA'** in the DataFrame.
Now, we **applied** those **functions** to the **graph**, in particular the largest connected component (LCC) is extracted. Then, the **'compute_CN_PA' function** is used to **calculate Common Neighbors and Preferential Attachment scores** for the LCC and the **'add_mean_column' function** is **applied to the DataFrame** containing CN and PA metrics. This **adds a new column representing** the **mean of the rescaled CN and PA values**.

## Understanding the code
### Insights and Interpretations
- *Rescaling*: Rescaling the 'CN' and 'PA' values to a 0-1 range normalizes these metrics, making them directly comparable regardless of their original scales or distributions. This is particularly useful when these metrics vary widely in scale or when combining them.

- *Mean of Scaled Values* : Computing the mean of 'CN_scaled' and 'PA_scaled' provides a single metric that balances the influence of both CN and PA. This can be useful for analyzing potential connections in the network by considering both the likelihood of connection (suggested by CN) and the network influence (indicated by PA).

This approach is beneficial in network analysis, especially in predictive modeling where a single, balanced metric might be more effective than using multiple metrics separately. For example, this combined metric could help identify potential new connections or influential nodes.

## *Finding top missing links*
We initialized a **'find_top_missing_links'** which **aim** is to **find the top 5 pairs of nodes** (potential missing links) in a DataFrame based on specified indices. First of all, we **created** an **empty dictionary** to **store** the **top missing links for each index**, this is done by **iterating** over the provided **list of indices**. Then it **sorts** and **select Top Links**: it is**sorted in descending order** based on the **current index and selects the top 5 rows**. This **sorting implies** that the **function is looking** for the **highest scores in each index**. It **extracts the node pairs** from the **'Node1' and 'Node2' columns** of the sorted DataFrame and **stores them** in the dictionary **under the corresponding index**.
nNow we **applied** teh **function in th graph**, providing it with the **list of indices** (e.g., 'CN', 'PA', 'Mean_CN_PA') to **look for top missing links**. Finally, we **identify** the **top 5 missing links** of our graph, by **calling the function** with the DataFrame and the list of indices. This step identifies the top 5 potential missing links in the network based on each index.

## Understanding the code
### Insights and Interpretations
- *Network Link Prediction*: The function is designed for link prediction in networks, a key task in network analysis. It identifies pairs of nodes that, based on certain metrics, are most likely to form a link.

-*Multiple Metrics for Prediction*: By using different indices (CN, PA, Mean_CN_PA), the function offers a multifaceted view of potential connections. Each index provides a different perspective:

- *CN (Common Neighbors)*: Suggests that nodes with many mutual connections are more likely to connect.
PA (Preferential Attachment): Implies that nodes with high degrees (many connections) are more likely to form new connections.

- *Mean_CN_PA*: A balanced metric combining both CN and PA perspectives.
Top Candidates for New Links: The top 5 pairs for each metric represent the most promising candidates for future links, based on the respective metric. This can guide efforts in network growth strategies, community detection, or even in understanding underlying structural tendencies of the network.

In summary, the find_top_missing_links function is a tool for identifying potential areas of growth or evolution within a network by highlighting the node pairs most likely to connect according to different network metrics.
