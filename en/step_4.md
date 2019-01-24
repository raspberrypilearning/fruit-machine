## Building A Basic Interface

Now that we have two buttons, one which flips a coin and one which rolls a die, we can combine them into a simple interface. We can do this using Grid.


--- task ---

Put the Buttons in the top row of the `Grid`, and the outputs in the bottom row.

```
Grid[
 {
  {dice = one;
   Button["Roll the Dice", 
    dice = RandomChoice[diceOptions]],
    
   coin = heads;
   Button["Flip the Coin", 
    coin = RandomChoice[coinOptions]]
   },
  
  {Dynamic[dice], Dynamic[coin]}
  }
 ]
 ```

--- /task ---
