# Assignment3

In this assignment, I performed various nearest neighbor search algorithms to identify the similar products (for a given product) using OnlineRetail dataset. 

#### Dataset : [link](https://archive.ics.uci.edu/ml/datasets/online+retail)
#### Colab: [link](https://colab.research.google.com/drive/1LJbNgoaacwfgiVNfkfJiekgfCd56zjJI?usp=sharing)


Below are more details about the algorithms.

## Locality Sensitive Hashing (LSH)

FAISS provides another index known as LSH to solve ANN search. LSH groups similar data points (or vectors) into the same bucket, using a hash function. LSH uses a hash function that results in higher collisions instead of minimal collisions (which is a general case in hashmap though).

After grouping the similar data points, LHS will only compare the search vector with other vectors from the same group that search vector belongs to. In this way, LSH compares the search vector with few number of vectors instead of all the vectors.

## Exhaustive search

Faiss (Facebook AI Similarity Search) has several methods for similarity search. In this, instances are represented as vectors and these vectors can be compared using Euclidean distance method. Vectors are considered as similar if they have lowest euclidean distance between them. In this way, the similar vectors are extracted for the given vector.

IndexFlatL2 method uses brute-force way to search for similarities using euclidean disatance method.

Faiss has two implementations of this operation:

Direct implementation i.e., using brute-force approach to loop over all the vectors, to find the most similar elements.
Second implementation is similar to the first implementation but uses BLAS library to calculate distance efficiently (via matrix/matrix multiplication), which makes this faster compared to the first approach
Below is an example of first implementation.

## Product quantization

Faiss loads the entire index (about vectors) into the RAM during the querying process, so exhaustive search works ONLY if the number of vectors OR it's dimensions, is not huge. In other words, it will be challenging to use exhaustive search for dataset with millions of vectors having huge number of dimensions.

In this case, we can use Faiss with Product Quantizer's compression algorithm to compress the indexed vectors. In this approach, vector size will be encoded to the specified number of bytes. As the stored vector is compressed, the distance calculated between the vectors will be a approximate value instead of an exact value. So, the similarities created using this approach will be of approximate similarities.

## Trees and graphs

Annoy (Approximate Nearest Neighbors Oh Yeah) is being used as recommendation engine by Spotify. Annoy constructs N binary trees, where each tree is independently constructed by recursively partitioning the data points. While searching for nearby neighbors, search process is carried out by travelling through tree nodes (starting from the root).

## HNSW

HNSW is an extension to navigable small world (NSW) graphs, where an NSW graph is a graph structure containing vertices connected by edges to their nearest neighbors.

Each node in the graph represents a vector point, and nodes are linked to other nodes that are close in space.

With a graph data structure on the data set, approximate nearest neighbors can be identified using graph traversal methods. For a given query, we find its nearest neighbors by starting at a random point in the graph and computing its distance to the given query. From this entry point, graph will be explored by calculating the distance to the query for each newly visited node (until no closer point is found).

HNSW-based ANNS is the highest performing index.


