---
title:  "How are trees saved in ranger?"
date:   2017-12-14
categories: ranger R
---

A frequently asked question is: "How are trees saved in ranger objects?"

Answer (taken from https://github.com/imbs-hl/ranger/issues/147):

`child.nodeIDs` is a list containing two vectors for each tree. These are the child node IDs for each node in the tree. The left children in the first vector, the right children in the second vector. The nodeIDs are 0-indexed. However, since the root of a tree (ID 0) cannot be a child, the 0 is used for terminal nodes. 

In `split.varIDs` there is a vector for each tree with the splitting variables for each node in the tree. These IDs are 0-indexed, too. If you use the formula interface, the 0-variable should be the outcome. Terminal nodes also have a 0 here. 

In `split.values` the splitting values for all nodes are saved. In terminal nodes, the outcome for this node is saved in `split.values`.

Note: A 0 in `split.varIDs` is no sufficient condition for a terminal node. Check `child.nodeIDs` to be sure. 

