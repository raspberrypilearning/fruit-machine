## Finishing Touches

Great! We now have two buttons. The first button rolls again, tells us if we won or lost, and updates the score. The second button starts the game again, resetting the scores back to 100.

Let's design the interface so that the two buttons are next to each other.

--- task ---
Put the buttons into a list, and then put the list inside the `Row` function.


```
roll = RandomChoice[fruits, 3];
result = Text["Click Roll Again to Start"];
Row[{Button["Roll Again",
   roll = RandomChoice[fruits, 3];
   result =
    Which[
     Max[Counts[roll]] == 3, Text[ "Winner!"],
     Max[Counts[roll]] == 2, Text[ "So Close!"],
     Max[Counts[roll]] == 1, Text[ "Loser!"]]
   ],
  Button["Start Again", score = 100]
  }]
Dynamic[Grid[{roll}, Frame -> All, FrameStyle -> Thick]]
Dynamic[result]
```
--- /task ---

