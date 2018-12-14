## Finishing Touches

Great! We now have two buttons. The first button rolls again, tells us if we won or lost, updates our score, and shows us a graph of our scores. And the second button starts the game again, resetting the scores back to 100.

--- task ---
It would be nice to have these buttons in one output cell, and in a horizontal line, so that it looks more like a game interface.
We can do that using Row. We put the buttons in a list, and then put that list inside Row.

```
roll = RandomChoice[fruits, 3];
result = Text["Click Roll Again to Start"];
score = 100;
scoreplot = {};
Row[{Button["Roll Again",
   roll = RandomChoice[fruits, 3];
   result =
    Which[
     Max[Counts[roll]] == 3, score += 10; Text[ "Winner!"],
     Max[Counts[roll]] == 2, score += 2; Text[ "So Close!"],
     Max[Counts[roll]] == 1, score -= 10; Text[ "Loser!"]];
   AppendTo[scoreplot, score]
   ],
  Button["Start Again", score = 100; scoreplot = {}]
  }]
Dynamic[Grid[{roll}, Frame -> All, FrameStyle -> Thick]]
Dynamic[result]
Dynamic[score]
Dynamic[ListPlot[scoreplot]]

```
--- /task ---