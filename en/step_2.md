## Make a Magic 8 Ball which selects answers at random

--- task ---
If you have never used the Wolfram Language before, follow [this guide to get started](https://projects.raspberrypi.org/en/projects/getting-started-with-mathematica) and learn to use the tool. Look at the sections **Starting Mathematica** and **Programming in Mathematica**.
--- /task ---

In this project, you will create a Magic 8 Ball, where the user can push a button and get an answer which is randomly selected from a list of possible answers.

--- task ---
Use the following code to create three lists of possible responses: a positive list, a negative list, and a neutral/non-committal list.

```
positives = {"It is certain.", "It is decidedly so.", 
   "Without a doubt.", "Yes, definitely.", "You may rely on it.", 
   "As I see it, yes.", "Most likely.", "Outlook good.", "Yes.", 
   "Signs point to yes."};
   
noncommittal = {"Reply hazy,try again",
   "Ask again later.", "Better not tell you now.", 
   "Cannot predict now.", "Concentrate and ask again."};
   
negatives = {"Don't count on it.", "My reply is no.", 
   "My sources say no.", "Outlook not so good.", "Very doubtful."};
   
```
--- /task ---

Then, use the `RandomChoice` function to select a response at random. 

```
RandomChoice[positives]
```
```
RandomChoice[noncommittal]
```
```
RandomChoice[negatives]
```

---task---
Next, use `Join` to put all of the possible responses into one list.

```
allresponses = Join[positives, noncommittal, negatives];
```
---/task---

To make the ouput nicer to use, create a button which lets the user interact better with the code. Use the following line of code to do this.

```
Button["Ask Again", Print[RandomChoice[allresponses]]]
```

--- task ---

At the moment, every time the user presses the button, the new answer appears underneath the previous answer. It would be better if the new answer replaced the old answer when the user presses the button.

You can use `Dynamic` to do this. `Dynamic` displays the updated value, so every time you press the button and rerun the code, `Dynamic` will display the new value and replace the old value.

Create a `Dynamic` button which gives a new random response every time the user presses it. You can use the following lines of code.

```
ans = "Focus hard on your question and ask the ball";
Button["Ask Again",
 ans = RandomChoice[allresponses]
 ]
Dynamic[ans]
```
--- /task ---
