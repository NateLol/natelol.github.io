---
title: "Neighbour Components Anaysis"
date: 2020-10-11T20:40:22+08:00
draft: false
author: "Guodong"
authorLink: 
license: 
images: []

tags: [nca]
categories: [ML]
featuredImage: "NCA.png"

hiddenFromHomePage: false
hiddenFromSearch: false
twemoji: false
lightgallery: true
ruby: true
fraction: true
fontawesome: true
linkToMarkdown: true
rssFullText: false


toc:
  enable: true
  auto: true
code:
  copy: true
math:
  enable: true
mapbox:
  accessToken: ""
share:
  enable: true
comment:
  enable: true
---

**Neighbour Components Analysis (NCA)** learns a linear transfromation for the input space such that in the transformed space, KNN performs well.





Let $Q = A^TA$, we have
$$
\begin{aligned}d(x,y) &= (x-y)^T Q (x-y) \\\\ &= (x-y)^TA^TA(x-y) \\\\&= (Ax-Ay)^T(Ax-Ay)\end{aligned}
$$
NCA proposes to use a softmax value to represent the probability that for a given sample $i$, sample $j$ is selected as its neighbour.
$$
p_{ij} = \frac{\exp(-||Ax_i - Ax_j||^2)}{\sum_{k \neq i} \exp(-||Ax_i - Ax_k||^2)}
$$
which is the pair similarity over all posible pairs, looking for the nearnest sample in the new space. We can see $A$ as a transformation and $Ax$ is the projected representation in a new feature space. 



Thus the overall objective is to find tha optimum $A$ such that,
$$
f(A) = \max_{A}\sum_{i}\sum_{j \in C_i}p_{ij}
$$


