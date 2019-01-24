## Adding Sentiment Analysis

Sentiment analysis is the attempt to classify 'happy' words and 'sad words' in a sentence, and then work out if the emotional tone behind the sentence was positive, negative or neutral.
Wolfram has a sentiment classifier built in. You can input a phrase or sentence, and it will classify the text as generally positive, negative or neutral.

![Sentiment Analysis](images/SentimentAnalysis.png)


--- task ---
Make an `InputField` so that users can input their question, and a `Button` to deliver a response. Keep the response random for now.

```
answer = "Concentrate on your question";
{InputField[Dynamic[question], String], 
 Button["Answer",
  Dynamic[answer = RandomChoice[allresponses]
   ]
  ]}
Dynamic[answer]

```

--- /task ---

Now let's build a a `Which` statement to choose a response based on how the sentiment analysis. If the sentiment is positive, we want our magic 8 ball to return a positive statement, if the sentiment is negative, we want the magic 8 ball to return a negative statement, and if the sentiment is neutral, we want to return a non commital statement.

A `Which` statement is similar to an If Else statement in other programming languages. It takes a series of possibilities, and instructions for what to do if that possibility is true. It will return the outcome of the first possibility which returns True.


 --- task ---
Build a `Which` statement which returns a random negative response to a negative sentiment question, a noncomittal response to a neutral sentiment question, and a positive response to a positive sentiment question.
 
 ```
 Which[
 Classify["Sentiment", question] == "Negative", 
 answer = RandomChoice[negatives],
 Classify["Sentiment", question] == "Neutral", 
 answer = RandomChoice[noncomittal], 
 Classify["Sentiment", question] == "Positive", 
 answer = RandomChoice[positive],
 ]
 ```

 --- /task ---
 
  --- task ---
Incorporate this Which statement into the `InputField` and `Button` interface.
 
 ```
 answer = "Concentrate on your question";
{InputField[Dynamic[question], String], 
 Button["Answer",
  Dynamic[Which[
    Classify["Sentiment", question] == "Negative", 
    answer = RandomChoice[Join[negatives, noncomittal]],
    Classify["Sentiment", question] == "Neutral",
    answer = RandomChoice[noncomittal], 
    Classify["Sentiment", question] == "Positive", 
    answer = RandomChoice[Join[positives, noncomittal]]
    ]
   ]
  ]}
Dynamic[answer]
```
 
  --- /task ---