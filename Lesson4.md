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

Names of functions are followed by this *thick arrow* which is our other special character. You can either use keyboard shortcut CTRL+3 or choose it from the list of characters in the *Menu/Insert*. Every procedure ends with a word **end**. I'll use tabs in the procedure because it is clearer and more convenient to read.

We want to refer to this procedure using **call** command. We can do it before or after we declare functions. I prefer having all functions at the end.

```
call ➤NewExcelFile
```

The first thing that this function will do is open the first file *data.xlsx*.

```
 excel.open path ♥datafile1 result ♥excelid1
 ```
 
All of the opened excel workbooks by G1ANT.Robot, have special ids set. So, we'll also add a result argument which lets us choose the name of the variable in which the id of the opened excel file is stored. The ids are useful when we want to switch between many different excel files.

I'll use **dialog** command to show you what the result is and how the id looks. 

```
dialog ♥excelid1
```

Let’s run this. In the pop-up window, some number should appear.
Now, let’s delete this line.

Let’s write this line to open new empty excel file.

```
excel.open result ♥excelid2
```

It'll be a lot easier if we add two more procedures. One which gets data from the first file, second which enters the data into another excel file.
We will name the first one as ➤GetValues, the second one as ➤SetValues.

```
procedure ➤GetValues


end

procedure ➤SetValues


end
```

**excel.switch** command lets us switch between excel files opened by G1ANT.Robot. We will need this command because we want to switch many times between *data.xlsx* and *data2.xlsx* files to get data, enter data, get data, enter data etc... Now we can use variable *excelid1* that we created at the beginning because we want to open a file with this id. 
