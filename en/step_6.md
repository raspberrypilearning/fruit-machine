## Keeping Score

Great, now we can press a button and automatically get a new roll and the result. But what if we want to keep score? We'd need a variable to keep track, and we'd need to have each result in the Which statement add or subtract from the score. You can choose to have your game assign any score to each result.
In order to add or subtract from a number, we set the variable:
```
number = 1
```
And then we can add using `+=`, and take away using `-=`

![Number Adding](images/NumberAdd.png)

--- task ---
Set up a score variable.

```
score = 100
```

--- /task ---

Within the Which function, we can make multiple actions happen if our question is true by using a ;. This is called a Compound Expression. So for each possibility, we can add to or subtract from the score.

Winning (when the `Max` is 3), should increase the score by 10. Losing (when the `Max` is 1) should decrease the score by 10. Getting close (when the `Max` is 2), should increase the score by 2.

Start off by creating a score variable, and decide how many points each action (winning, getting 2, and losing) will gain/lose.

--- task ---

Add the score changes to your Which statement using a ;


```
result =
  Which[
   Max[Counts[roll]] == 3, score += 10; Text[ "Winner!"],
   Max[Counts[roll]] == 2, score += 2; Text[ "So Close!"],
   Max[Counts[roll]] == 1, score -= 10; Text[ "Loser!"]];

```
Replace your previous code for `result` with your new `Which` statement.

--- /task ---

We will also need a way to reset the score.

--- task ---
Create another button which sets the score back to 100.

```
Button["Start Again", score = 100; scoreplot = {}]

 ```
 --- task ---

