`eightButton =` 
![Magic 8 Ball](images/8Ball.png)

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
allresponses = Join[positives, noncomittal, negatives];

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
