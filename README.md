# Load-Balanced-LSH

Motivation: 
Classic LSH constructs unbalanced structure which naturally leads to inefficient searching. While our Load-Balanced LSH obtains balanced buckets, so the average number of image candidates returned by LBLSH is small, thus drastically accelerating the detection.

Procedure: 
initialization, basic hashing, local redistribution and neighbor-probe searching.

Details of local redistribution step: 
After the Basic Hashing operation, we need to find the virtual center V C for every bucket, whose d-dimension coordinates are the average values of the current items in the bucket. Then, we will check every bucket according to its position in the hash table. If the size ni(t) of a bucket exceeds its threshold ∆LB, we need to compute the distance between its each item and its V C, and sort the items by their distances in descending order. Then (ni(t) − ∆LB) items are chosen with the farthest distance, and these chosen items will be sent to neighbor buckets. In order to guarantee the stability of the hash buckets and the accuracy of detection, the virtual center V C for every bucket is pre-computed after Basic Hashing, and not updated during the iteration. If the iteration goes to the last bucket in a hash table and its size exceeds ∆LB, the chosen farthest items will be sent to the first bucket, and the iteration will start over again from the first bucket. When all buckets conform the ∆LB constraint, we finish the LBLSH construction.
