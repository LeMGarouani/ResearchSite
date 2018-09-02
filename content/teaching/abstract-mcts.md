+++
# Date this page was created.
date = "2017-11-05"

# Project title.
title = "Abstract MCTS"
slide_link = "/sources/teaching-example/abstract-mcts/abstract-mcts.md"

# Project summary to display on homepage.
summary = "Abstract simple implementation of Monte Carlo Tree Search (UCT) using Upper Confidence Bound (UCB) algorithm developed in C++. An example is available to show how implements it."

# Optional image to display on homepage (relative to `static/img/` folder).
#image_preview = "projects/post-it-yellow.jpg"

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["machine-learning"]

# Optional external URL for project (replaces project detail page).
external_links = [
      [
        "https://github.com/jbuisine/MCTS", "Github", "project", "blue"
      ]
    ]

# Does the project detail page use math formatting?
math = false

# Optional featured image (relative to `static/img/` folder).
[header]
#image = "headers/bubbles-wide.jpg"
caption = "Abstract MCTS"

+++


# Description

Abstract simple implementation of Monte Carlo Tree Search (UCT) using Upper Confidence Bound (UCB) algorithm developed in C++. An example is available to show how implements it.

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

## Contributors

* [jbuisine](https://github.com/jbuisine)

## Licence

[MIT](https://github.com/jbuisine/MCTS/blob/master/LICENSE)
