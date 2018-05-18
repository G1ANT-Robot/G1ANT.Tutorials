Welcome to the 5th lesson!

You’ve learned so much so far that this time we’ll try to do a little more complicated automation. Finally, a web one!
Our aim is to fill in the following table in excel using data from [x-rates.com](https://x-rates.com/) in Internet Explorer.

The excel template is available [here](update_currency.xlsx).

Firstly, we should create a new variable containing the path to this file.

```
♥dataFile = ‴C:\Users\wikto\Documents\Currencies\update_currency.xlsx‴
```

Very often we need to use other programming languages in G1ANT.Robot such as C#, JQuery or JavaScript because it is helpful or easy to us.
In this type of automation, we have to focus on algorithms in a website. 
When we have a little more complex automation to do, it is better to firstly come up with the best idea how to do it before we write anything.

Let’s investigate the x-rates.com website. Look at the url for Polish Zloty rates table: [http://www.x-rates.com/table/?from=PLN&amount=1](http://www.x-rates.com/table/?from=PLN&amount=1).

We see that there is “from=PLN” section and probably when we put there a different currency, we’ll have another rates table.
Let’s paste there GBP to find out if we were right. [http://www.x-rates.com/table/?from=GBP&amount=1](http://www.x-rates.com/table/?from=GBP&amount=1). We’ve noticed an algorithm. So, to fill in the GBP, PLN and any other currency table that might be written in this excel sheet, we can just simply create a loop.

In this big loop there should be another loop to go row by row by firstly filling in the Today Column, then the Yesterday Column and last the Percent Change Column. There are other ways to do this automation, of course, but we’ll try to do this this way because it is easy.

As you probably imagine, it is best to create one main function (procedure) and probably three other which will get data from this website and then set them to the corresponding columns in excel.

Okay, once we have the general idea, we can start to code.
Let’s create one main function that I will name simply a Process.

```
call ➤Process

procedure ➤Process



end
```
Let’s open **♥dataFile**.

```
call ➤Process

procedure ➤Process
    excel.open ♥dataFile


end
```

Now, we set a label to create a loop in which we will fill in the whole table of GBP, then PLN etc.

```
    excel.open ♥dataFile
    ➜getCurrFrom
    
    jump ➜getCurrFrom
```

The first thing that we want to do is get value from the merged cells in the first row C-E. To access these data with G1ANT.Robot, we have to get value from the first cell on the right because that is where the value is.

The number of row is not going to change within this loop but number of column – yes. So, let’s create **♥currFromCol** variable set to 3 before our loop because we don’t want our loop to reset the value for this variable each time the loop is done. It should increase each time by 3 because there are 3 of merged cells (column Today, Yesterday and Percent Change). Our result is going to be stored in **♥currFrom** variable.

```
    ♥currFromCol = 3
    ➜getCurrFrom
            excel.getvalue row 1 colindex ♥currFromCol result ♥currFrom
            ♥currFromCol = ♥currFromCol + 3
    jump ➜getCurrFrom
```

Let’s create three more procedures to fill each of those columns separately.

```
procedure ➤GetAndSetTodayValues




end

procedure ➤GetAndSetYesterdayValues
    
    
    
end

procedure ➤CalculatePercentChange
    
    
    
end
```

Let’s come back to our main function **➤Process**. We need to call these three functions here to let our loop **➜getCurrFrom** fill in these three columns.

```
➜getCurrFrom
            ♥row = 3
            excel.getvalue row 1 colindex ♥currFromCol result ♥currFrom
            call ➤GetAndSetTodayValues
            call ➤GetAndSetYesterdayValues
            call ➤CalculatePercentChange
            ♥currFromCol = ♥currFromCol + 3
    jump ➜getCurrFrom
```

Let’s add a **window** command to see how all the tables will be filling in by our Robot. Excel commands can work without bringing excel windows to the front that’s why this command is needed.

```
    window ‴update_currency - Excel‴
    excel.getvalue row 1 colindex ♥currFromCol result ♥currFrom
```

To get the name of one window, we can simply open Tools, click Windows in the Menu or use CTRL+W shortcut, find a window that we are interested in and copy it. On the image below, look at the highlighted part.

As you probably know, we have a never-ending loop between 8-14 lines. Let’s do something with it. The loop should end if the value in the first row is empty (there is no currency that we want to convert from).

If we set the condition in the 14th line after **jump** command, we would also have to add another **excel.getvalue** before. But it would cause the G1ANT.Robot to get this currency value two times (once at the end of the loop and once at the beginning) and we do not want to do that. So, we will simply add a **➜finish1** label inside this loop.

```
➜getCurrFrom
            ♥row = 3
            window ‴update_currency - Excel‴
            excel.getvalue row 1 colindex ♥currFromCol result ♥currFrom
        jump ➜finish1 if ⊂string.IsNullOrEmpty(♥currFrom)==true⊃
            call ➤GetAndSetTodayValues
            call ➤GetAndSetYesterdayValues
            call ➤CalculatePercentChange
            ♥currFromCol = ♥currFromCol + 3
    jump ➜getCurrFrom
        jump ➜finish1
```

I have already formatted the code (added tabs). Let’s use C# macro and inside these *special round brackets* ⊂⊃ insert C# expression which allows us to get to know if there is another currency in the specified cell to convert from. If not, the script will jump to **➜finish1** label. 

Finally, we can fill other procedures. What we have to do first, in the **➤GetAndSetTodayValues** is to open x-rates.com in the Internet Explorer. Remember what we’ve noticed about this website? We’ve seen that there is an algorithm in how the webpage’s links are made.  Let’s use this information and do this:

```
procedure ➤GetAndSetTodayValues
    ie.open ‴http://www.x-rates.com/table/?from=♥currFrom&amount=1‴
    
    
end
```
**♥currFrom** variable contains name of currency that we want to convert from therefore we can just use this variable inside this webpage link.

In this procedure we also want to have a loop. Let’s create a **➜GetAndSetTodayValues** label.

```
ie.open ‴http://www.x-rates.com/table/?from=♥currFrom&amount=1‴
➜getAndSetTodayValues


jump ➜getAndSetTodayValues
```
In every procedure that gets and sets data into excel file, there has to be a **♥row** variable initially set to 3 because in all 3 procedures we start with row 3. So, let’s add this line in the main procedure **➤Process**. (look at the 9th line)

```
procedure ➤Process
    excel.open ♥dataFile
    ♥currFromCol = 3
    ➜getCurrFrom
            ♥row = 3
            window ‴update_currency - Excel‴
            excel.getvalue row 1 colindex ♥currFromCol result ♥currFrom
        jump ➜finish1 if ⊂string.IsNullOrEmpty(♥currFrom)==true⊃
            call ➤GetAndSetTodayValues
            call ➤GetAndSetYesterdayValues
            call ➤CalculatePercentChange
            ♥currFromCol = ♥currFromCol + 3
    jump ➜getCurrFrom
        jump ➜finish1
end
```
Let’s come back to the **➤GetAndSetTodayValues** procedure. We want to bring the excel window to the front, get value from “B” column to get to know the name of a currency that we want to convert to (we will name the result variable **♥toCurr**) and end this loop when there will be no more currencies in the “B” column. So, we type:

```
procedure ➤GetAndSetTodayValues
ie.open ‴http://www.x-rates.com/table/?from=♥currFrom&amount=1‴
    ➜getAndSetTodayValues
            window ‴update_currency - Excel‴
            excel.getvalue row ♥row colname b result ♥toCurr
        jump ➜finish2 if ⊂string.IsNullOrEmpty(♥toCurr)⊃
        
        
    jump ➜getAndSetTodayValues
        ➜finish2
end
```

Now we have to get the data from this website. How to do it?
We need to explore the x-rates.com again.

Let’s right click on the converted value from GBP to USD for instance. Then choose “Inspect element” to open Developer Tools. This is what we obtain: (how to attach image??)

As you can see this element on the website can be found by “href” using this link in quotes. Let’s see if we are right. Click on the Console and using JQUERY expression, find this converted currency value.

As you can see, comparing obtained values to those above in the table, we know that there is an algorithm which we can use in our automation.
Using **ie.runscript** command and entering these JQUERY expressions as argument values will get us the result we want. Don’t know if I already told you so but we do not have to set the name of the variable where we store the results. It will be named by default a **♥result**.

```
ie.runscript ‴$('a[href="/graph/?from=♥currFrom&to=♥toCurr"]').eq(0).text()‴
```

Now we have to convert the result value to float type (type which allows us to have numbers with decimal places).

```
 ♥TodayValue = ⟦float⟧♥result
 ```
 
The last thing is to set new variable **♥TodayCol** to **♥currFromCol** just to make our code clearer next time we come back to it, set **♥TodayValue** to the specified cell and increase **♥row** by 1 because this loop fill is in Today Column row by row.

```
➜getAndSetTodayValues
            window ‴update_currency - Excel‴
            excel.getvalue row ♥row colname b result ♥toCurr
        jump ➜finish2 if ⊂string.IsNullOrEmpty(♥toCurr)⊃
            ie.runscript ‴$('a[href="/graph/?from=♥currFrom&to=♥toCurr"]').eq(0).text()‴
            ♥TodayValue = ⟦float⟧♥result
            ♥TodayCol = ♥currFromCol
            excel.setvalue value ♥TodayValue row ♥row colindex ♥TodayCol
            ♥row = ♥row + 1
    jump ➜getAndSetTodayValues
```

Let’s reset the variable ♥row back to 3 and close Internet Explorer.

```
    ♥row = 3
    ie.close
```

I don’t think we need to go through ➤GetAndSetYesterdayValues step by step as with the previous one because it is very similar.

The main thing that differs is the webpage link for yesterday values. Example:
[http://www.x-rates.com/historical/?from=GBP&amount=1&date=2018-02-28](http://www.x-rates.com/historical/?from=GBP&amount=1&date=2018-02-28) 

Probably we can access other webpages like this by changing only the date and currency. You can check if it is right, but I assure you that it is :).

In order to get the yesterday date, we can just add the following line of code at the beginning with the C# expression.

```
♥yesterday = ⟦text⟧System.DateTime.Now.AddDays(-1).ToString("yyyy-MM-dd")
```

This is show the ➤GetAndSetYesterdayValues should look.

```
procedure ➤GetAndSetYesterdayValues
    ie.open ‴http://www.x-rates.com/historical/?from=♥currFrom&amount=1&date=♥yesterday‴
    ➜getAndSetYesterdayValues
            excel.getvalue row ♥row colname b result ♥toCurr
        jump ➜finish3 if ⊂string.IsNullOrEmpty(♥toCurr)⊃
            ie.runscript ‴$('a[href="/graph/?from=♥currFrom&to=♥toCurr"]').eq(0).text()‴
            ♥YesterdayValue = ⟦float⟧♥result
            ♥YesterdayCol = ♥currFromCol + 1
            excel.setvalue value ♥YesterdayValue row ♥row colindex ♥YesterdayCol
            ♥row = ♥row + 1
    jump ➜getAndSetYesterdayValues
        ➜finish3
    ♥row = 3
    ie.close
end
```

Let’s finish the last procedure that is left.
Firstly, we should set new variable ♥percentChangeCol to ♥YesterdayCol increased by 1.

```
procedure ➤CalculatePercentChange
    ♥percentChangeCol = ♥YesterdayCol + 1
    
end
```

To calculate percent change we do not have to open x-rates.com because we already have all the needed values.

Now, let’s create a loop as in the previous procedures and make it not never-ending (remember we have to get value from the specified cell and set the condition that if there is no currency, stop the loop).

```
    ➜calculatePercentChange
            excel.getvalue row ♥row colindex ♥TodayCol result ♥todayValue
        jump ➜finish4 if ⊂string.IsNullOrEmpty(♥todayValue)⊃
            
            
    jump ➜calculatePercentChange
        ➜finish4
 ```
 
 After we get value from “Today” column, we should get also value from “Yesterday”.
 
 ```
 excel.getvalue row ♥row colindex ♥YesterdayCol result ♥YesterdayValue
 ```
 
 Now we can calculate the percent change:
 
 ```
 ♥percentChange = ‴=((♥todayValue - ♥YesterdayValue)/♥todayValue)‴
 ```
 
 Finally, let’s set value and increase variable ♥row by 1.

This is the end of this Currency automation! 

Thank you and hope to see you again.


**Whole code:**
```
♥dataFile = ‴C:\Users\wikto\Documents\Currencies\update_currency.xlsx‴
♥yesterday = ⟦text⟧System.DateTime.Now.AddDays(-1).ToString("yyyy-MM-dd")
call ➤Process
procedure ➤Process
    excel.open ♥dataFile
    ♥currFromCol = 3
    ➜getCurrFrom
            ♥row = 3
            window ‴update_currency - Excel‴
            excel.getvalue row 1 colindex ♥currFromCol result ♥currFrom
        jump ➜finish1 if ⊂string.IsNullOrEmpty(♥currFrom)==true⊃
            call ➤GetAndSetTodayValues
            call ➤GetAndSetYesterdayValues
            call ➤CalculatePercentChange
            ♥currFromCol = ♥currFromCol + 3
    jump ➜getCurrFrom
        jump ➜finish1
end
procedure ➤GetAndSetTodayValues
    ie.open ‴http://www.x-rates.com/table/?from=♥currFrom&amount=1‴
    ➜getAndSetTodayValues
            window ‴update_currency - Excel‴
            excel.getvalue row ♥row colname b result ♥toCurr
        jump ➜finish2 if ⊂string.IsNullOrEmpty(♥toCurr)⊃
        ie.runscript ‴$('a[href="/graph/?from=♥currFrom&to=♥toCurr"]').eq(0).text()‴
        ♥TodayValue = ⟦float⟧♥result
        ♥TodayCol = ♥currFromCol
        excel.setvalue value ♥TodayValue row ♥row colindex ♥TodayCol
        ♥row = ♥row + 1
    jump ➜getAndSetTodayValues
        ➜finish2
    ♥row = 3
    ie.close
end
procedure ➤GetAndSetYesterdayValues
    ie.open ‴http://www.x-rates.com/historical/?from=♥currFrom&amount=1&date=♥yesterday‴
    ➜getAndSetYesterdayValues
            excel.getvalue row ♥row colname b result ♥toCurr
        jump ➜finish3 if ⊂string.IsNullOrEmpty(♥toCurr)⊃
            ie.runscript ‴$('a[href="/graph/?from=♥currFrom&to=♥toCurr"]').eq(0).text()‴
            ♥YesterdayValue = ⟦float⟧♥result
            ♥YesterdayCol = ♥currFromCol + 1
            excel.setvalue value ♥YesterdayValue row ♥row colindex ♥YesterdayCol
            ♥row = ♥row + 1
    jump ➜getAndSetYesterdayValues
        ➜finish3
    ♥row = 3
    ie.close
end
procedure ➤CalculatePercentChange
    ♥percentChangeCol = ♥YesterdayCol + 1
    ➜calculatePercentChange
            excel.getvalue row ♥row colindex ♥TodayCol result ♥todayValue
        jump ➜finish4 if ⊂string.IsNullOrEmpty(♥todayValue)⊃
            excel.getvalue row ♥row colindex ♥YesterdayCol result ♥YesterdayValue
            ♥percentChange = ‴=((♥todayValue - ♥YesterdayValue)/♥todayValue)‴
            excel.setvalue value ♥percentChange row ♥row colindex ♥percentChangeCol
            ♥row = ♥row + 1
    jump ➜calculatePercentChange
        ➜finish4
end
```
