## A Random Magic 8 Ball

You will build a magic 8 ball, where the user can push a button and get an answer randomly selected from a list of possible answers.

--- task ---

Create three lists of possible responses: a positive list, a negative list, and a neutral/noncomittal list.

```
positives = {"It is certain.", "It is decidedly so.", 
   "Without a doubt.", "Yes-definitely.", "You may rely on it.", 
   "As I see it,yes.", "Most likely.", "Outlook good.", "Yes.", 
   "Signs point to yes."};
   
noncomittal = {"Reply hazy,try again",
   "Ask again later.", "Better not tell you now.", 
   "Cannot predict now.", "Concentrate and ask again."};
   
negatives = {"Don't count on it.", "My reply is no.", 
   "My sources say no.", "Outlook not so good.", "Very doubtful."};
   
```
--- /task ---

In order to choose a response at random, we use the `RandomChoice` function. 

```
RandomChoice[positives]
```
```
RandomChoice[noncomittal]
```
```
RandomChoice[negatives]
```

---task---
`Join` all the possible responses into one list.

```
allresponses = Join[positives, noncomittal, negatives];
```
---/task---

It would be nice if we could have a button which lets us interact better with the code.

```
Button["Ask Again", Print[RandomChoice[allresponses]]]
```

The problem with this is that every time you press the button, it prints another answer under the previous one. It would be better if the new answer replaced the previous answer. In order to do this, we need to set up a `Dynamic` variable for the answer, which updates whenever you press the button.

--- task ---
Create a `Dynamic` button which gives us a new random response each time we press it.

```
ans = "Focus hard on your question and ask the ball";
Button["Ask Again",
 ans = RandomChoice[allresponses]
 ]
Dynamic[ans]
```
--- /task ---
