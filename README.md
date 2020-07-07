# Bloom Filter False Positives


## Introduction

Although **Bloom Filters** (BF) have been widely used in many networking applications and beyond, the fundamental issue of how to calculate the false positive probability remains elusive. Properly calculating the false positive probability of BF is critical because it is used to calculate the optimal number of hash functions k. Since Bloom gave the false positive formula in 1970, in 2008, Bose et al. pointed out that Bloom’s formula for calculating the false positive probability is flawed and gave a new false positive formula; and in 2010, Christensen et al. further pointed out that Bose’s formula is also flawed and gave another new false positive formula. Although Christensen’s formula is perfectly accurate, it is time-consuming to calculate the false positive probability, and it is impossible to calculate the derivation of the optimal value of k. While the conventional wisdom is to derive the optimal value of k from a false positive formula, in this paper, we propose the first approach to calculating the optimal k without any false positive formula. Our approach is based on the following observation: for a BF with m bits and n elements, if and only if its entropy is the largest, its false positive probability is the smallest, according to information entropy theory. Furthermore, we propose a new and more accurate upper bound for the false positive probability. When the size of a Bloom filter becomes infinitely large, our upper bound turns equal to the lower bound, which becomes Bloom’s formula. This deepens our understanding of Bloom’s formula: it is perfectly accurate when m is infinitely large, and it is practically accurate when m is sufficiently large. Besides, we derive the bounds of correct rate of counting Bloom filters (one widely used variant of BFs for estimating item frequencies) by applying our proposed formulas about BFs to them. 


## About the source code, dataset and parameters setting 

The source code contains the C++ implementation of the standard Bloom filter and counting Bloom filter. 
We complete these codes on Linux 14.04.5 and compile successfully using g++ 4.8.4. 

The file **distinctIP_sample.dat** and **IP_sample.dat** is the subset of the anonymized IP trace collected in 2016 from CAIDA used in experiments.
The dataset distinctIP_sample.dat contains 4M distinct elements totally. 
The dataset IP_sample.dat contains 1M distinct elements and their corresponding frequencies totally. 


The parameters setting is the same as mentioned in the paper.


## How to run

Suppose you've already cloned the respository and start from the `bfcode` directory.

You just need:

	$ make
	$ ./main


## Output format

### BF test:
| n | k | m | emprical fp probability | Bloom's fp probability | Bose's upper bound | our upper bound | Bose's bounds error ratio | our bounds error ratio | Bose's optimal k | our optimal k |
| - | - | - | ----------------------- | ---------------------- | ------------------ | --------------- | ------------------------ | ---------------------- | ---------------- | ------------- |

### CBF test:
| n | k | m | emprical correct rate | upper bound of correct rate | lower bound of correct rate |
| - | - | - | --------------------- | --------------------------- | --------------------------- |
