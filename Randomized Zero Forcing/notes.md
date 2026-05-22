# Understanding Papers: Randomized Zero Forcing

cover: ![chicken.gif](images/chicken.gif)
excerpt: Understanding the paper "Randomized Zero Forcing", by Jesse Geneson, Illya Hicks, Noah Lichtenberg, Alvin Moon, and Nicolas Robles.
tags: Understanding Papers, Discrete Mathematics
prerequisites:

## Introduction

Welcome to the understanding papers series. This is an article about [Randomized Zero Forcing](https://arxiv.org/pdf/2602.16300), a paper by Jesse Geneson, Illya Hicks, Noah Lichtenberg, Alvin Moon, and Nicolas Robles. It's never as hard as you think!

## Understanding Graphs

We're not actually talking about the algebra graphs this time. No coordinates or x or y axis. This time, we're talking about this kind of graphs: 

![drawing-2026-05-22T05-47-01-291Z.png](images/drawing-2026-05-22T05-47-01-291Z-light.png)

Looks big and complicated, but a graph is just dots and lines. That's it. You don't need a bigger understanding of graphs for this paper. 

What's nice to know though, is a **directed graph**. Same thing as above, but imagine the lines are arrows instead. 

![drawing-2026-05-22T05-48-42-056Z.png](images/drawing-2026-05-22T05-48-42-056Z-light.png)

This describes friendships for example-person A might think person B is a friend, but person B might think otherwise. In that scenario, A would point to B, but B wouldn't point to A. If they're both homies tho they'd have bidirectional arrows and point to each other. 

## Zero Forcing

Now, let's get to the rudimentary part of the paper. Zero Forcing. 

You know Conway's Game of Life? Imagine that, but much simpler. 

Imagine you pick some dots in a graph to be blue, and the other ones, white. Now, the blue dots can INFECT white dots to become blue, but only if a blue dot has ONLY ONE white dot as a neighbor. 

![drawing-2026-05-22T05-57-06-719Z.png](images/drawing-2026-05-22T05-57-06-719Z-light.png)

In this situation, in one **round**, 2 would become blue because 7's only white neighbor is 2. Nothing else would become blue, because 6 has 4 white neighbors (including 2) and 8 has 2 white neighbors. Since 7 only has 1 white neighbor, that white neighbor becomes blue. Like a zombie apocalypse where the zombies gang up on humans only if they have only one human to focus on. Otherwise they get distracted and don't bite anyone. A zombie who chases more than 1 human catches none. 

## Probabilistic Zero Forcing

Now this one is even more like a zombie apocalypse. Imagine the same game (Zero Forcing), but instead of this rule of a blue dot only needing one white dot neighbor, you implement a **probability** system, where there's a chance of any white dot becoming blue. 
