# Graph Neural Networks with PyG

## Graph Machine Learning

Machine learning (ML) on a graph fundamentally differs from ML on
two-dimensional data (such as images or structured tables) primarily
due to the **irregular structure** and **relational nature** of graph
data, which necessitates specialized models and data representations.

Here is a breakdown of the differences based on data characteristics
and the resulting ML pipeline requirements:

### 1. Data Structure and Relationship

The core distinction lies in the organization of the input data:

*   **Two-Dimensional Data:** Data like images or certain structured
	data often possesses a **regular structure** (e.g., a grid for
	images or a sequence for time series). Traditional deep learning
	models like Convolutional Neural Networks (CNNs) are specialized
	for computer vision applications dealing with these images,
	leveraging inherent **spatial locality**.
*   **Graph Data:** Graphs are a general language for describing
	entities and their **relations and interactions**. Graph data is
	characterized by its **irregular structure**. The central problem
	in ML on graphs is finding the right way to incorporate the
	**information about the graph structure**—the relational
	structure—into the machine learning model.
*   **Data Storage:** Graph data requires specific formats to store
	this relational information, such as:
	*   A matrix containing the **features of every node**.
	*   A representation of the **graph connectivity**, often called
		the `edge_index`. This matrix specifies the source and
		destination of every edge.
	*   Optional **edge features** (e.g., weights or attributes).
	*   The graph data can also be complex, often being massive,
		messy, constantly changing, and sometimes **heterogeneous**
		(having more than one node type or more than one edge type) or
		**temporal** (changing over time) in real-world applications.

### 2. Traditional ML Feature Engineering

In traditional ML pipelines for graphs, significant effort must be
placed on creating features that capture the topological context, a
step often less critical or handled differently for standard tabular
or image data:

*   **Feature Focus:** Traditional ML pipelines on graphs require two
	steps: first, representing the data points (nodes, links, or
	entire graphs) with vectors of features, and second, training a
	classical ML classifier on those vectors. The predictive
	performance depends heavily on creating **structural features**
	that describe how a particular node is positioned in the network
	and what its local network structure is.
*   **Handcrafted Features:** This process traditionally relies on
	**handcrafted features** to capture the relational structure of
	the network. Examples of structural features for nodes include:
	*   **Importance-based features:** Node degree or centrality
		measures (like eigenvector centrality, betweenness centrality,
		or closeness centrality).
	*   **Structure-based features:** Clustering coefficients
		(measuring connectivity among neighbors) or **graphlet degree
		vectors** (counting the number of times a pre-specified
		subgraph, or graphlet, appears rooted at a given node).

### 3. Deep Learning Approaches (GNNs vs. CNNs)

Graph Neural Networks (GNNs) are designed to handle the irregular
structure of graphs and overcome the need for non-trivial human
feature engineering.

*   **Core Operation:** The fundamental operation in GNNs, graph
	convolutions, is known as **message passing**. Message passing
	involves aggregating the features of a node's neighbors to update
	that node's representation. This process takes node features (X)
	and the connectivity matrix (`edge_index`) as inputs.
*   **Feature Aggregation:** GNN layers aggregate the features of
	neighbors using methods ranging from fixed weights to attention
	mechanisms. For tasks like classifying an entire graph (e.g.,
	classifying a protein structure), a **pooling function** (such as
	Global add pool) is used to sum up the information from all nodes
	in the graph.
*   **Model Input and Processing:** Unlike CNNs processing 2D grid
	data, GNNs must handle the complex and sparse nature of graph
	connections. Frameworks like PyTorch Geometric manage this by
	using sophisticated tensor structures (like the `edge_index`
	tensor) and optimized operations (like sparse matrix
	multiplications, or SPMs) designed specifically for data with lots
	of zeros, which is typical for graphs.

## Wait, what's a graph?
The basic features of a graph, how data is mapped to them, and the
resulting advantages stem from the graph's ability to natively
represent entities and their complex, irregular relationships.

### 1. Basic Features of a Graph Structure

A graph is a general language for describing **entities**, their
**relations**, and **interactions**. When storing graph data for
machine learning, the structure requires specific components:

**Core Data Components (PyTorch Geometric Context):**
1.  **Node Features ($X$ or $data.x$):** A matrix containing the
	features or attributes of every node. These features must
	generally be of a numerical type (float, double, or integer).
2.  **Graph Connectivity (`edge_index`):** This special format defines
	the connections (edges) between nodes. It is typically a matrix of
	two rows, where the first row writes the **source** of every edge
	and the second row writes the **destination**.
3.  **Edge Features (`edge_attribute`):** Optional features that
	describe the edges themselves, such as weights or multiple
	attributes.
4.  **Target ($Y$ or $data.y$):** The target values used for training,
	which can be flexible depending on whether the task involves
	classification for every node, every edge, or the entire graph.

**Structural Features (Derived Properties):** In traditional machine
learning on graphs, good predictive performance relies on engineering
**structural features** that describe the network topology. These
features capture how a node is positioned and what its local structure
is:

*   **Importance-Based Features:** Capture the influence or position
	of a node in the graph:
	*   **Node Degree:** The number of edges connected to a node,
		which is a useful but simple feature.
	*   **Node Centrality Measures:** Characterize the importance of a
		node, including **eigenvector centrality** (importance based
		on the importance of neighbors), **betweenness centrality**
		(importance as an important connector lying on many shortest
		paths), and **closeness centrality** (importance based on
		having small shortest path lengths to all other nodes).
*   **Structure-Based Features:** Capture the local neighborhood
	topology:
	*   **Clustering Coefficient:** Measures how connected a node's
		neighbors (friends) are. It basically counts the number of
		**triangles** in the node's immediate network.
	*   **Graphlet Degree Vector (GDV):** A generalization of triangle
		counting that counts the number of times a pre-specified,
		rooted, connected, non-isomorphic subgraph (a **graphlet**)
		appears rooted at a given node. The GDV provides a
		fine-grained measure of local topological similarity between
		nodes.

### 2. How Tabular Data Can Be Mapped to Graph Properties

Tabular or relational data can be mapped to graph features by
identifying entities as nodes and relationships as edges.

**Example: Social Network Data Mapping:** If tabular data describes
people in a social network, the mapping could be structured as
follows:

| Tabular Data Component | Graph Property | Example Content |
| :--- | :--- | :--- |
| Individual Entity (Person) | **Node** | Person 1, Person 2, Person 3, Person 4 |
| Individual Attributes | **Node Features ($X$)** | Age (e.g., 42 years old) and Income Level (e.g., 1200 currency). |
| Relationship/Interaction | **Edge ($\text{edge\_index}$)** | An edge exists between two people if they know each other. |
| Relationship Strength | **Edge Attributes** | The weight of the edge could be the time (e.g., years) that both people have met each other. |
| Prediction Target | **Target Label ($Y$)** | The hours that person is working now. |

**Example: Relational Databases (RDL):** More complex structured data,
like an entire SQL database, can be treated as a graph for
**Relational Deep Learning (RDL)**. In this scenario:

*   **Entities** (e.g., database records) become **nodes**.
*   **Primary/foreign key links** become **edges**.
*   The nodes can handle multimodal data, including numbers,
	categories, and free text.

### 3. What is Gained by Performing this Mapping

The primary gain of mapping data onto a graph structure is the ability
to incorporate and leverage the **relational structure** inherent in
the data, moving beyond traditional models that assume data regularity
or independence.

**Key Advantages:**

1.  **Capturing Relational Structure:** The central challenge and
	benefit of ML on graphs is explicitly incorporating the
	**information about the graph structure** (the relational
	structure) into the model. This relational structure is crucial
	for obtaining **good predictive performance**.
2.  **Addressing Irregularity:** Graphs serve as a powerful
	representation because they can model interactions and relations
	that do not fit into the regular structures assumed by traditional
	deep learning (like the grid structures used for images by CNNs).
3.  **Advanced Representation Learning:** Graph Neural Networks (GNNs)
	utilize the graph structure to learn effective representations for
	nodes, links, or entire graphs. This process, often involving
	**message passing** (aggregating neighbor features), overcomes the
	need for complex, **hand-designed features** that were required in
	older, traditional ML pipelines on graphs.
4.  **Enabling Relational Deep Learning (RDL):** Mapping relational
	data to a graph allows for modern deep learning models (GNNs) to
	learn directly on raw relational databases, enabling breakthroughs
	in practical domains.
5.  **Augmenting Language Models (Graph RAG):** Graphs can be used in
	Retrieval Augmented Generation (RAG) pipelines for Large Language
	Models (LLMs) by providing crucial relational and **topological
	information**. Using GNNs to encode subgraphs and feed this
	structural context to an LLM can significantly enhance accuracy
	(in one scenario, leading to a 2x increase in accuracy compared to
	the LLM alone).
6.  **Predicting Links and Roles:** Graph features are essential for
	specific relational tasks, such as predicting new links between
	nodes (link prediction) or predicting a particular node's role in
	the network (e.g., predicting protein function) using
	structure-based features like Graphlet Degree Vectors.

## Mapping Brain Data With a Graph Network

### Strucutral MRI

Modeling structural brain data, such as a 3D volumetric MRI, with a
graph learning approach involves **transforming the regular, spatial
data structure into an irregular, relational structure** that captures
the entities (brain regions) and their interactions (connectivity).

Graphs provide a general language for describing **entities,
relations, and interactions**. Since the fundamental challenge in
machine learning (ML) on graphs is finding the right way to
incorporate the **relational structure**, mapping brain data to a
graph explicitly enables the ML model to utilize these connectivity
patterns.

Here is how structural brain data could be mapped onto the basic
features of a graph:

#### 1. Defining Nodes (Entities)

The entities in a structural brain graph would be the different
functional or anatomical regions of the brain.

*   **Mapping:** Each distinct region of the brain (often defined by
	an atlas or parcellation scheme) becomes a **node**.
*   **Context:** Graph nodes represent the basic data points of
	interest.

#### 2. Defining Node Features ($X$)

Node features are numerical attributes attached to each entity. For
structural MRI data, these features would be the metrics describing
the structural properties of the defined brain region.

*   **Mapping:** The node features ($X$ or $data.x$) would be a vector
	of metrics extracted from the 3D MRI volume for that specific
	region.
	*   These features could include structural measures such as
		volume, cortical thickness, gray matter density, or even
		complex statistics of tissue intensity within that region.
*   **Requirement:** Only features of a numerical type (float, double,
	or integer) are allowed in the feature tensor.

#### 3. Defining Edges and Connectivity (`edge_index`)

The edges describe the relationships or connections between the brain
regions. In neuroscience, these often represent structural
connections.

*   **Mapping:** An **edge** would be placed between two nodes
	(regions) if a meaningful connection exists.
	*   If the structural data includes information about white matter
		tracts (e.g., from Diffusion Tensor Imaging, which is often
		used alongside MRI), the edges would represent the presence
		and characteristics of these physical tracts connecting the
		regions.
	*   The **graph connectivity** is stored in a special format
		called `edge_index`, typically a matrix of two rows specifying
		the source and destination of every edge.
*   **Edge Attributes:** Optional **edge features (`edge_attribute`)**
	could be used to quantify the connection, such as the estimated
	strength, length, or fiber count of the white matter tract between
	the two regions.

#### 4. Defining the Prediction Target ($Y$)

The target ($Y$ or $data.y$) depends on the specific machine learning
task.

*   **Graph-Level Task:** Predicting a property of the whole brain
	structure. For example, using the resulting structural brain graph
	to classify an entire subject as belonging to a clinical group
	(e.g., diseased vs. healthy).
*   **Node-Level Task:** Predicting a property of an individual brain
	region. For example, predicting a particular region's functional
	role or classifying it based on localized pathology.

#### Gains of the Graph Mapping Approach

While 3D volumetric MRI data inherently has a **regular structure**
similar to 2D image data (which is typically handled by Convolutional
Neural Networks, or CNNs), modeling it as a graph provides critical
advantages for biomedical analysis:

1.  **Capturing Relational Structure:** The most significant gain is
	explicitly incorporating the **information about the graph
	structure**—the complex relational structure of brain
	connectivity—into the model. Traditional models designed for
	regular grids struggle to natively encode these non-local, sparse,
	and intricate topological relationships.
2.  **Specialized Deep Learning:** The graph representation enables
	the use of specialized models like Graph Neural Networks (GNNs),
	which use **message passing** (aggregating features from connected
	neighbors) to learn representations that naturally capture both
	the attributes of a region and its relational context within the
	network.
3.  **Handling Complexity:** The approach aligns with applications in
	other complex scientific domains, such as mapping out **complex
	molecular structures** and **protein-protein interaction
	networks** in biomedicine. The structure of the brain network
	itself is the key to obtaining **good predictive performance** in
	these relational learning tasks.

### Working with functional (MRI, EEG / MEG, etc) data as a graph

fMRI and EEG are more similar to **time series data**
or **temporal data**, and can be modeled using specialized graph networks
and the supporting frameworks.

Graph networks serve as a general language for analyzing entities and
the relationships and interactions between them. When dealing with
data that changes over time, like time series, the structure can be
captured using **temporal graphs**.

Here is how time-varying data can be conceptualized and managed within
a graph network framework:

### 1. Modeling Dynamic Relationships

Modeling time series data requires capturing the evolving structure of
the relationships, which can be done through **temporal graphs**
(graphs that change over time).

*   **Necessity for Temporal Support:** Real-world data is often
	dynamic, and networks, such as transaction networks or social
	networks, frequently evolve over time.
*   **Framework Support:** Frameworks like PyTorch Geometric (PyG) 2.0
	have introduced robust native support for **temporal graphs** to
	conquer the complexities of real-world graph data.

### 2. Handling Temporal Information and Sampling

To process a time series dataset modeled as a temporal graph,
techniques focusing on preserving the time order are crucial:

*   **Temporal Subgraph Sampling:** PyG 2.0 provides support for
	**temporal subgraph sampling** for both homogeneous and
	heterogeneous graphs.
*   **Respecting Constraints:** This technique allows the traversal of
	dynamic graphs over time, extracting snapshots that must strictly
	respect **temporal constraints**. This is essential to prevent
	**future information leakage** because you only see data available
	up to a specific timestamp.
*   **Querying Historical Data:** The design includes supporting the
	querying of **historical subgraphs**, where samplers can iterate
	over external seed nodes and timestamps while always respecting
	the temporal order.
*   **Sampling Strategies:** Various temporal sampling strategies are
	offered, including uniform, most recent K elements, or
	annealing-based strategies.

### 3. Graph Structure and Feature Assignment

When designing the graph network for time series data, the entities
(like sensors or measurement points) and their interactions would be
defined:

*   **Nodes and Features:** Entities become **nodes**. Each node can
	have features attached to it via a **tensor assignment**. For
	example, a matrix containing the features of every node is stored
	as `X`.
*   **Edges and Connectivity:** The relationships or correlations
	between these entities form the connections (links). The graph
	connectivity is stored in a special format called `Edge\_index`,
	which is a matrix of two rows (source and destination).
*   **Edge Features (Weights):** Edge attributes (features) can also
	be stored, such as edge weights or multiple weights for every
	edge, often in the `edge\_attribute` matrix.
*   **Prediction Tasks Over Time:** Modeling over time is often done
	for **link prediction** tasks, where the objective is to predict
	new links based on the existing network structure. This can
	involve predicting links that will appear in the future (e.g.,
	between time $T_{0}$ and time $T_{0'}$), which is highly relevant
	for networks evolving over time.
