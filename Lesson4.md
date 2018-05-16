Welcome to the 4th lesson!

Today we are going to learn how to use procedures to make our code more ordered and structured and how to create loops to avoid having too many lines of code.

We'll upgrade our previous program. Firstly, let’s delete file *data2.xlsx* which we’ve previously created via G1ANT.Robot. It is most convenient when we have two tabs opened at the same time (our previous script and a new one that will be based on the previous one - from lesson 3).

So, let's paste the two needed paths as we had before. 

```
♥datafile1 = ‴C:\Users\a\Downloads\data.xlsx‴
♥datafile2 = ‴C:\Users\a\Downloads\data2.xlsx‴
```

Procedures are functions in our programming language. Sometimes the automation is so long and complicated that dividing the whole script into small pieces and naming every step is almost necessary. We'll start with creating one main function which will refer to other functions that we will add:

```
procedure ➤NewExcelFile

end
```

