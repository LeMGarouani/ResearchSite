layout: true
<div class="remark-header"><span><a href="" class="remark-quit-cross"><i class="fas fa-times fa-2x"></i></a></span></div>
<div class="remark-footer"><span>Abstract MCTS
<a href="https://github.com/jbuisine/MCTS" class="remark-icon-bottom"><i class="fab fa-github fa-1x"></i></a>
</span></div>

---
class: center, middle
# Abstract MCTS
<hr>
**Summary** : Abstract simple implementation of Monte Carlo Tree Search (UCT) using Upper Confidence Bound (UCB) algorithm developed in C++. An example is available to show how implements it.

---

## Installation

It's a cmake project, so if you want to run example you only need to :

```commandline
mkdir build
```

```commandline
cd build
```

And then :
```commandline
cmake ..
```

---

## How to use

If you want to implement your own version of MCTS
```c++
#include TreeNode.h
```

You have to define the abstract methods :
- expand() : how you expand your problem (depend of your context)
- rollOut(TreeNode _node) : what is your simulation and roll out returned
- getBestChild() : what is for you the best child result

Note that by default, TreeNode abstract class use UCB selection :
- select() : selection method of next node to explore (UCB1 formula currently)

---

## Contributors

* [jbuisine](https://github.com/jbuisine)

---

## Licence

[MIT](https://github.com/jbuisine/MCTS/blob/master/LICENSE)
