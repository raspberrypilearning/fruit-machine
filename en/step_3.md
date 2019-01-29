## Random Choices

The game requires three random fruits from the pile.

In order to choose fruits at random, we use the `RandomChoice` function. 

```
RandomChoice[fruits]
```

We can get a list of random choices by calling `RandomChoice` a number of times.

![Random Choice](images/RandomChoice.png)

--- task ---

Use `RandomChoice` to generate a list of three random fruits taken from our `fruits` list.

```
RandomChoice[fruits, 3]

```

--- /task ---

We can also improve how this looks. At the moment, we have lots of coding elements, like `{}` and `,` which we don't necessarily want in our output.

--- task ---

 Put the output into a `Grid`, with a `Frame`, which lets us present them much like a real fruit machine.

```
Grid[{RandomChoice[fruits, 3]}, Frame -> All, FrameStyle -> Thick]
```

![Making a Grid](images/Grid.png)

--- /task ---