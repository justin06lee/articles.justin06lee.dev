# Machine Learning for the Blind

cover:![meme.png](images/meme.png)

excerpt: For those who know the neural network graph thing but don't ACTUALLY know what any of it means
tags: Machine Learning, Beginner
prerequisites:

## Introduction

I never understood machine learning. They show all of these diagrams of neural networks and I always took that at surface value. So I am going to do a deep dive and actually start understanding these things. 

## Wait, it's all floats?

Yup, it's all floats. This diagram you see:

![drawing-2026-04-20T23-31-28-146Z.png](images/drawing-2026-04-20T23-31-28-146Z-light.png)

Is a LIE. All the circles are just straight up actual numbers, and the lines are also numbers.

What does this mean? Exactly what it means. 

literally

```txt
float neuron = 0.5;
```

That's what those circles are. The same with the lines. They're literally randomly selected floating point numbers with a tiny little bit of added complexity.

That's what gets you chat gpt and claude. Crazy stuff.

Anyhow, let's "build" a "project". Let's say we wanna have a model that detects whether or not some image is that of a cat. we have multiple inputs. So instead of making more variables by hand, let's use an array: 

```txt
float inputs[3] = {0.9, 0.3, 0.7}
// very pointy ears, smallish animal, fluff
```

That's it. The comments is what the inputs represent. On a scale from 0.0 to 1.0, how pointy are the ears? Take a look at this: 

![drawing-2026-04-20T23-47-20-548Z.png](images/drawing-2026-04-20T23-47-20-548Z-light.png)

Those are very pointy ears. In fact, I would say that they're about 9/10. But since we're talking about 0.0 to 1.0, I'll say 0.9/1.0. I'm assuming it's pretty small (0.3/1.0) and just cuz I drew it and i'm biased, it's 0.7/1.0 fluffy. idk how to draw fluff

Anyhow, now we have 3 inputs. 

I'll explain the difference between inputs and neurons a little further down—don't worry about the difference just yet.

Now let's make some weights. A weight is just a number that indicates how relevant each input is. 

```txt
float weight[3] = {0.8, 0.1, 1.0}

// pointy ears are important (weight[0] = 0.8)
// there are big cats and small cats so this doesn't matter that much (weight[1] = 0.1)
// and fluff is (OBVIOUSLY) very very important (weight[2] = 1.0)
```

Ok. So what exactly did we just make?? Well, *technically* we didn't actually make neurons.

```txt
float inputs[3] = {0.9, 0.3, 0.7}
```

These three aren't *neurons*, they're *inputs*. It's just cuz we put the numbers (0.9, 0.3, 0.7) in there ourselves. It was never *computed* by anything else we just thought the ears were pointy and the cat, fluffy.

In order to *actually* create our first **neuron** we have to do some computations. Remember the weights? 

```txt
float weight[3] = {0.8, 0.1, 1.0}
```

We can use the inputs with the weights and make some calculation that means something: 

If the cat's ears are this (0.9) pointy, and pointiness matters this (0.8) much, doesn't it kinda make sense if we just multiply these two numbers?

And then we can do this for all the inputs and their corresponding weights. The cat is this (0.3) big, and size (of the cat) only matters this (0.1) much. The cat is this (0.7) fluffy, and fluffiness matters this(1.0) much. 

Now we can add all the multiplied values together like this:

```txt
Result = (0.9 * 0.8) + (0.3 * 0.1) + (0.7 * 1.0) = 1.45
```

It doesn't have to be between 0 and 1 btw these are random values I made up and the result happens to be 1.45. But since this is hard to interpret (145% a cat???) we use something called a sigmoid function to squish the value to a percentage point (between 0 and 1). 

This is how the sigmoid works: 

```txt
// Big positive number -> close to 1
// Big negative number -> close to 0
// zero -> 0.5

float sigmoid(float x) {
    return 1.0 / (1.0 + exp(-x));
}
```
but that looks kinda scary so

let me put it into math format:

$$
\sigma(x) = \frac{1}{1+e^{-x}}
$$

(the lil symbol thing is sigma 🗿)

this function, when graphed, looks like this: 

![drawing-2026-04-21T00-18-36-332Z.png](images/drawing-2026-04-21T00-18-36-332Z-light.png)

Which means whatever x you input, it'll be between 0 and 1. Higher the x, closer f(x) is to 1. Lower the x into negative, the closer f(x) is to 0. 

Anyway now if we put the number we got (1.45) into the sigmoid function we get:


$$
\sigma(1.45) = \frac{1}{1 + e^{-1.45}}
$$

$$
\sigma(1.45)= \frac{1}{1+2.72^{-1.45}}
$$

$$
\sigma(1.45)= \frac{1}{1.23}
$$

$$
\sigma(1.45)= 0.81
$$

The numbers were rounded but you get the point. Kids' stuff. 

Now our model, based on 

```txt
float input[3] = {0.9, 0.3, 0.7}
```
this and 

```txt
float weight[3] = {0.8, 0.1, 1.0}
```
this, thinks that there's an 81% chance that we were in fact describing a cat.

Here's the code you can play with for your very first, bare bones, fully manual neural network model: 


```py
import math

inputs = [0.9, 0.3, 0.7]
# pointy ears, size of animal, fluff

weights = [0.8, 0.1, 1.0]
# pointy ears is important, size not so much, fluff very much so

result = 0.0
# init result var

for i in range(len(inputs)):
    result += inputs[i] * weights[i]
    # add (0.9 * 0.8) + (0.3 * 0.1) + (0.7 * 1.0) to results

sigma = (1/(1 + math.e ** (-1 * result)))
# sigmafy results to become percentage

print(sigma)
# print sigmafied result

```
