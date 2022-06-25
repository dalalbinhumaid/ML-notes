# Decision Trees
Mon, 23 May 2022 at 17:19
#entropy #information #gain #classification
## Overview
#### Definition
> "A decision tree is a decision support tool that uses a tree-like model of decisions and their possible consequences, including chance event outcomes, resource costs, and utility. It is one way to display an algorithm that only contains conditional control statements" [wikipedia](https://en.wikipedia.org/wiki/Decision_tree#:~:text=A%20decision%20tree%20is%20a,only%20contains%20conditional%20control%20statements.)


Used for ==classification==  and when dealing with continuous output [regression trees](https://medium.com/analytics-vidhya/regression-trees-decision-tree-for-regression-machine-learning-e4d7525d8047#:~:text=A%20regression%20tree%20is%20basically,outputs%20instead%20of%20discrete%20outputs.)  are used instead.
#### input
`dataset` with attributes and class output. Input variables can be both **discrete** or **continuous**.
#### Output 
`probability scores` of class membership
`a tree` where its leaves are the probability score or each class value

## Use Cases
Mostly used when a series of yes/no questions most be answered to arrive at the classification.  Examples:
- Biological species classification
- Patient symptoms evaluation

When if/then conditions are needed.  Examples:
- Predicting customers segments
- Loan/mortgage approvals
- Fraud detection 
## Decision Trees Terminology
#### structure
Decision trees are a flow-chart representation of if/then statements.
1. ==*Root Node*== &rarr; top node
2. ==*Internal Nodes*== &rarr; decision nodes
3. ==*Leaf Nodes*== &rarr; class labels
4. ==*Branches*== &rarr; decision output
5. ==*Depth*== &rarr; no. of branches from current node to root 
	1. a `stump` is a tree of depth 1

> 
![[Pasted image 20220523180155.png]]

---
#### Algorithm 
1. ==*Purity*== &rarr; probability of the corresponding class based on the node's decision
	1. 100% **purity** when all of the node's data belongs to `one` class
	2. 100% **impurity** when the node's data is evenly split *same records of each class* 
2. ==*Splitting rules*== &rarr; defines how a decision tree is split

## Tree Induction Algorithm
### First: choose the most informative feature
Two ways to choose whether an attribute is informative or not:
1. *Gini Index* - used in [[#CART Algorithm]]
	$$ Gini_x = 1-\sum_{\forall x\in X}{P(x)^2} $$
2. *Entropy* - measures the `impurity` of an attribute. You first find the **base entropy** of the current dataset then find each attribute's **conditional entropy**. Finally, you calculate the **information gain** and `choose the most informative feature`
	$$ _{Base\,Entropy} \quad H_X = -\sum_{x\in X}{P(x) \log_2P(x)}$$
	$$ _{Conditional\,Entropy} \quad H_{Y|X} = -\sum_{x\in X}P(x) \sum_{y \in Y}P(y|x)\log_2 P(y|x)$$
	$$ InfoGain = H_X - H_{Y|X}$$
	- The minimum value of entropy is 0 which means the node is pure
	- The maximum value of entropy is $\log_2 k\,\,\,;\,\,\,k = no.\,of \,classes$
		- when the maximum value of entropy is reached; all classes are ==equally probable==
	
			 |       |  |
			| ----------- | ----------- |
			| impurity **&uarr;** | entropy **&uarr;** |
			| purity **&darr;**     | entropy **&uarr;** |


### Second: split according to the feature
### Third: repeat until split is pure 
#### Other algorithms
##### ID3 Algorithm
##### C4.5 Algorithm
##### CART Algorithm
## Pros & Cons

 | Reasons to Choose |  Cautions | 
 | :-- | -- |
 | Takes any input type | Axis-aligned|
 | Robust with redundant/correlated variables |Structure is sensitive to small changes in training data |
 | Can handle non-linear variables | Can easily over-fit the data as depth increases |
 | Computationally efficient | Does not handle missing values well |
 | Easy to score and understand | Decision rules can be very complex |

