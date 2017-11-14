# Calabash Brothers

<img src="calabash.jpg" width=300>

There are N calabash brothers numbered with 1, 2, ..., N. Each of them has a skill, which they may choose to use or not. So eash of them has two states: positive if he uses the skill and negative if not. For example, if K use his skill, his state is +K, otherwise -K. When the N brothers come together, they can create a new calabash brother, called Diamond brother, numbered with 0. Diamond is a fusion of N brothers and he is incredibly powerful, though he has no skill and only one state. The brothers including Diamond form tree structures, and Diamond is the root. So they are connected by hidden directed edges, which has different weights. The edge weights depend on the two associated brothers and their states. Whenever they form a new tree, the power of Diamond has an addition, which is the product of edge weights in the tree. The total power of Diamond is the summation of all the additions of all the different trees. We wonder how to choose the states of N brothers such that the total power of Diamond is as large as possible.

## Input

The first line is an integer N. In the following 4N<sup>2</sup>-2N lines, each line has 3 numbers U, V, W, which means the weight of the edge from U to V is W.

## Output

The output has only one line, which contains N integers of the states of our choices, separated by a space.

## Sample

The sampel with the following input has 2 calabash brothers and a Diamond. There are 4 possible choices: -1, -2; -1, +2; +1, -2; +1, +2. The corresponding total power is as follows.

| Choices | All Trees | Total Power |
|:-------:|:--------------:|:-----------:|
| -1, -2 | <img src="img/00.png" width=300> | 0.1x0.1 + 0.3x0.3 + 0.1x0.3 = 0.13 |
| -1, +2 | <img src="img/01.png" width=300> | 0.1x0.3 + 0.4x0.2 + 0.1x0.4 = 0.15 |
| +1, -2 | <img src="img/10.png" width=300> | 0.2x0.4 + 0.3x0.1 + 0.2x0.3 = 0.17 |
| +1, +2 | <img src="img/11.png" width=300> | 0.2x0.2 + 0.4x0.4 + 0.2x0.4 = 0.28 |

When we choose +1, +2, we get the maximum total power 0.28. So we should output +1 +2.

### Sample Input
```
2
-1 -2 0.1
-1 +2 0.3
+1 -2 0.4
+1 +2 0.2
-2 -1 0.3
-2 +1 0.1
+2 -1 0.2
+2 +1 0.4
0 -1 0.1
0 +1 0.2
0 -2 0.3
0 +2 0.4
```

### Sample Output
```
+1 +2
```

## Evaluation

Your score of the problem positively correlates with the total power of your output.

## Hints

After the states determined, all the chosen states and Diamond form a graph, and the total power is the number of spinning trees (treating the weight of edge as the number of edge), which can be found in O(N<sup>3</sup>) time by Matrix Tree Theorem.

The tractable exact solver maybe doesn't exist. We can employ variant approximation methods. The following is some ideas.

### Randomized Algorithms

Randomly generate some choices, and then output the maximum total power of them.

### Greedy Algorithms

Maintain a chosen state set and the fringe from the set to the legal others. First insert 0 into the set, and then greedily choose the maximum edge in the fringe.

### Local Search

Randomly initialize a choice, and then iteratively try to change some states in the choice to make the total power larger.

### Dynamic Programming

Choose a tree structure of brothers first, and then find the best states in the tree using dynamic programming.
