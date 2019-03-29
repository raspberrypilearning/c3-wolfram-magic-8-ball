## Design the user interface

Now, create a user interface, so that the display is clean, clear, and interesting.

--- task ---
Drag the image below into your notebook and assign the image to variable name `eightButton`.

![Magic 8 Ball](images/magiceightball.png)
--- /task ---
 
--- task ---
+ Change the button so that it looks like a Magic 8 Ball, instead of it saying 'Answer'.
+ Use `Appearance->None` to remove the frame around the button.
+ Use `Column` to present your interface.
+ Use the `Text` function to make the output strings look like text instead of code.

You can use the following code to do this.

```
answer = Text["Concentrate on your question"];
Column[{question = "Will I get home for Christmas?";
  InputField[Dynamic[question], String],
  Button[eightButton,
    Which[
     Classify["Sentiment", question] == "Negative",
     answer = RandomChoice[negatives],
     Classify["Sentiment", question] == "Neutral",
     answer = RandomChoice[noncommittal],
     Classify["Sentiment", question] == "Positive",
     answer = RandomChoice[positives]
     ],
   Appearance -> None]
  }]
Dynamic[Text[answer]]
```

To get a new response, the user needs to type a new question into the `InputField` and press the button.

 --- /task ---

Congratulations, you have made a smart Magic 8 Ball, which takes the user's feelings into account!
