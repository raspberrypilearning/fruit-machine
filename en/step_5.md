## Advanced Interface: Functions and Manipulations

What if we want to flip multiple coins, or roll multiple dice, at the same time?
In order to do this, we need to use `Manipulate`.

First, let's build a quick `Manipulate` interface which gives us the option to flip up to five coins.

In order to return multiple coins, we can ask `RandomChoice` to run multiple times:

```
RandomChoice[coinOptions, 5]
```
We can get rid of the `{}` and `,` using `Grid`.

```
Grid[{RandomChoice[coinOptions, 5]}]
```

We can then use `Manipulate` to allow the user to choose how many coins to flip. We do this by replacing the number with a variable, and then telling `Manipulate` what options to give the user to replace the variable.

--- task ---
Create a `Manipulate` which gives the user the option to flip between 1 and 5 coins.

```
Manipulate[
Grid[{RandomChoice[coinOptions, i]}],
{i, {1,2,3,4,5}}]
```
--- /task ---

We can do the exact same thing with the dice.

--- task ---

Create a `Manipulate` which gives the user the option to roll between 1 and 5 dice.

```
Manipulate[
Grid[{RandomChoice[diceOptions, i]}],
{i, {1,2,3,4,5}}]
```

--- /task ---

What if we want to have a single `Manipulate` function which allows the user to either flip a certain number of coins, or roll a certain number of dice?
One way to do this is to set up three functions, one for coins, one for dice, and one to choose which action (of coins and dice) we want to do.

We use `:=` to create a function using `SetDelayed`. `SetDelayed` lets us set the left hand side of the function to mean the right hand side. So then whenever we see the left hand side used, the code evaluates the right hand side in that place.

Functions need to have a variable. In this case, we want the variable to be how many times we roll the die or flip the coin.

--- task ---
Create two functions using `:=`. 

```
coins[a_] := Grid[{RandomChoice[coinOptions, a]}]; 
rolls[a_] := 
 Grid[{RandomChoice[{one, two, three, four, five, six}, a]}];
 ```
 --- /task ---
 
 You can test your functions by running a number through them:
 
 ```
 coins[3]
 ```
 
 ```
 rolls[5]
 ```
 
 Now we need a function which lets us choose which (of coins or rolls) we want to do.
 
 --- task ---

Create a function called action, using a `Which` statement to let the user choose between running the coins function or the rolls function.

The fucntion will need two input variables: the number of times we want to roll (a), and the type of roll we want (n).

If n is "Coins", then we run the coins function, and if n is "Dice", then we run the rolls function.
 
 ```
 action[n_, a_] := 
  Which[
  n == "Coins", coins[a],
  n == "Dice", rolls[a]
  ];
```

 --- /task ---
 
 
  --- task ---
Build a Manipulate with these three functions. 

We want to run action with the possible choices for n being "Coins" or "Dice", and possilbe choices for a being the numbers between 1 and 5.
 
 ```
 Manipulate[
 action[n, a], 
 {n, {"Coins", "Dice"  }},
 {a, {1, 2, 3, 4, 5}}]
 ``` 
 
 You can replace the two `Manipulates` you made with this sinlge `Manipulate`.
 --- /task ---