Welcome to the 5th lesson!

You’ve learned so much so far that this time we’ll try to do a little more complicated automation. Finally, a web one!
Our aim is to fill in the following table in excel using data from [x-rates.com](https://x-rates.com/) in Internet Explorer.

The excel template is available [here](update_currency.xlsx).

Firstly, we should create a new variable containing the path to this file.

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
