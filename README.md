# Frag-Shell-Algorithm

This code is being done as the assignment of CS 412- Intro to Data Mining (Spring 2018), University of Illinois at Urbana Champaign.

Rules for this assignment are mentioned below.

Input Format

The input dataset can have upto 26 categorical attributes, A, B, ..., Z. Each categorical attribute can have upto 9 different values. The possible values of an attribute X are represented using x1, x2, etc. For example, if attribute B has 3 possible values, then these values are represented using b1, b2, b3. Note that, all possible values of an attribute may not appear on the dataset.

The first line of input will be the number of partitions k. You can assume that number of attributes will be a multiple of k.

Each following line of input will contain one row of the dataset that will list the values corresponding to the attributes. You can assume that each row will have values for all attributes, i.e., no missing attribute. Also, all rows will follow the same ordering of attributes. For example, if the first row lists the value corresponding to attribute C first, and then lists the value corresponding to attribute A, all following rows will do the same. Here is a sample input.

2
a1 b2 c1 f2 d1 e1
a1 b2 c1 f2 d2 e1
a1 b2 c1 f2 d1 e2
a2 b1 c1 f2 d1 e2
a2 b1 c1 f2 d1 e3

Here, the number of partitions is 2. The dataset has six attributes, A, B, C, F, D, E and five rows. The first row has a1 as the value for A, b2 as the value for B, c1 as the value of C, f2 as the value of F, d1 as the value of D and finally e1 as the value of E.

Constraints

Your program must complete within the hackerrank imposed time limit.

Output Format

The output is the fragmented shells generated by the frag shells algorithm.

The fragmentation/partitioning of attributes needs to be done based on their ordering at input. For example, the sample dataset lists attributes A, B, C, F, D, E, and k is 2; therefore, the first partition will be {A, B, C}, and the second partition will be {F, D, E}.

For each partition, you need to generate all non-empty cells for all cuboids. For example, for partition {F, D, E}, the cuboids will be {F}, {D}, {E}, {F, D}, {F, E}, {D, E}, {F, D, E}. For each of these cuboids, you need to generate the non-empty cells.

You need to print the cells of cuboids as per the ordering of partitioning, i.e., first printing the cells corresponding to first partition, then printing the cells corresponding to second partition, and so on. The cells of any two partitions should be separetd by an empty line.

A cell is described by a list of values for different attributes and the support. For example, the cell F = f2, D = d1 is described as f2 d1 : 4. Here, the 4 after colon is the support of the cell, i.e., there are 4 rows where F = f2, D = d1. Note that, the values are listed as per the order of attributes at input. For example, F = f2, D = d1 is written as f2 d1 : 4 because attribute F appears before attribute D in the dataset.

The cells corresponding to any partition should be printed one cell per line, as per the following ordering rules. (i) Cells from coarser granularity cuboids need to appear before the cells from finer granularity cuboids. For example, for partition {F, D, E}, the non-empty cells corresponding to cuboids {F}, {D}, {E} need to appear before the non-empty cells corresponding to cuboid {F, D}, {F, E}, {D, E}. Similarly, the non-empty cells corresponding to cuboids {F, D}, {F, E}, {D, E} need to appear before the non-empty cells corresponding to cuboid {F, D, E}. (ii) For cells from cuboids of same granularity, the ordering of cells is determined based on the ordering of attributes at input. For example, for partition {F, D, E}, {F} < {D} < {E}, and {F, D} < {F, E} < {D, E}. This is because F appears before D, which appears before E at input. (ii) Finally, for cells within the same cuboid, the ordering is determined based on the attribute value combination. For example, for the cells of cuboid {D, E}, d1 e1 < d1 e2 < d1 e3 < d2 e1. Similarly, for the cells of cuboid {F, D, E}, f2 d1 e1 < f2 d1 e2 < f2 d1 e3 < f2 d2 e1. Notice that, the ordering is a combinatorial ordering (not a lexicographical one).

Here's the output corresponding to our sample input.

a1 : 3
a2 : 2
b1 : 2
b2 : 3
c1 : 5
a1 b2 : 3
a2 b1 : 2
a1 c1 : 3
a2 c1 : 2
b1 c1 : 2
b2 c1 : 3
a1 b2 c1 : 3
a2 b1 c1 : 2

f2 : 5
d1 : 4
d2 : 1
e1 : 2
e2 : 2
e3 : 1
f2 d1 : 4
f2 d2 : 1
f2 e1 : 2
f2 e2 : 2
f2 e3 : 1
d1 e1 : 1
d1 e2 : 2
d1 e3 : 1
d2 e1 : 1
f2 d1 e1 : 1
f2 d1 e2 : 2
f2 d1 e3 : 1
f2 d2 e1 : 1
