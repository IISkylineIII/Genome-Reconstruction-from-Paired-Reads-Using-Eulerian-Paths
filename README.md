# Genome-Reconstruction-from-Paired-Reads-Using-Eulerian-Paths

This Python script reconstructs a genome sequence from paired (k,d)-mers by constructing and traversing a De Bruijn graph. It identifies an Eulerian path through the graph to reconstruct the original genome while accounting for the specified gap between k-mers.

# Features
* Parses paired k-mers from input data.
* Builds a De Bruijn graph from paired (k,d)-mers.
* Identifies start and end nodes to define an Eulerian path.
* Uses randomized cycle finding to approximate Eulerian traversal.
* Reconstructs the genome sequence by aligning prefix and suffix overlaps.
* Handles the (k,d)-mer gap constraint during reconstruction.

# Usage

Define the parameters:

 * k: length of each k-mer.

 * d: gap distance between the two k-mers in each pair.

Provide a list of paired reads in the format:
* pairs = [('GAGA', 'TTGA'), ('TCGT', 'GATG'), ...]

Call reconstructGenome(pairs, k, d) to obtain the reconstructed sequence.


# Example
```
k = 4
d = 2
pairs = [
    ('GAGA', 'TTGA'),
    ('TCGT', 'GATG'),
    ('CGTG', 'ATGT'),
    ('TGGT', 'TGAG'),
    ('GTGA', 'TGTT'),
    ('GTGG', 'GTGA'),
    ('TGAG', 'GTTG'),
    ('GGTC', 'GAGA'),
    ('GTCG', 'AGAT')
]

result = reconstructGenome(pairs, k, d)
print(result)
```


# How it Works
* Graph Construction: Creates a directed De Bruijn graph where each node represents the prefix of a paired (k,d)-mer and edges indicate valid transitions between nodes based on suffix-prefix overlaps.
* Start and End Detection: Calculates node in-degree and out-degree to detect imbalances, allowing identification of a valid path start and end.
* Cycle Detection: Performs random cycle discovery across the graph to iteratively build a full Eulerian path.
* Genome Assembly: Reconstructs the genome by merging overlapping k-mers from both sides of the pairs, accounting for the distance d between them.

# Applications
* Assembly of genome sequences from paired-end read data.
* Educational demonstration of De Bruijn graphs and Eulerian paths.
* Foundation for developing more advanced genome assembly algorithms.

# License
This project is licensed under the MIT License.
