BJ Fogg is a american social scientist who proposed a model in which behavior is defined by the combination of three factors: motivation, ability and prompt.

In this model:

- If a person lacks motivation, they won’t perform the behavior, even if it's easy and there's a prompt.
- If a person lacks ability (it's too difficult), they won't do it, even if they're motivated and prompted.
- If there's no prompt, the behavior won't happen, even if they have motivation and ability.

The graph representation would look like this, where above the curve the prompt is successful, and otherwise it isn't.


```functionplot
---
title: B = MAP
xLabel: Motivation
yLabel: Ability
bounds: [0,10,0,10]
disableZoom: true
grid: false
---
f(x) = 1/((1/5)x)
```
