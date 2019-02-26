## Designing the User Interface

Let's create a user interface, so that the results are presented cleanly, clearly, and interestingly.

--- task ---
Drag the image below into your notebook and assign the image to variable name `eightButton`.

![Magic 8 Ball](images/magiceightball.png)
--- /task ---
 
--- task ---
+ Change the button to look like a magic 8 ball instead of saying 'Answer'.
+ Remove the frame around the button using `Appearance->None`.
+ Present your interface using `Column`.
+ Make the output strings look like text instead of code using the `Text` function.

```
answer = Text["Concentrate on your question"];
Column[{question = "Should I have pizza for breakfast?";
  InputField[Dynamic[question], String], 
  Button[eightButton,
   Dynamic[
    Which[
     Classify["Sentiment", question] == "Negative", 
     answer = RandomChoice[negatives],
     Classify["Sentiment", question] == "Neutral", 
     answer = RandomChoice[noncomittal], 
     Classify["Sentiment", question] == "Positive", 
     answer = RandomChoice[positives]
     ]
    ],
   Appearance -> None]
  }]
Dynamic[Text[answer]]
```

In order to get a new response, you need to type a new question into the `InputField` and press the button.
 --- /task ---

Congratulations, you have made a smart Magic Eight Ball, that's sensitive to your feelings!
