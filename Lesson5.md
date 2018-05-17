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
