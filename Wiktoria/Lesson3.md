Welcome to the third lesson!

This time we will automate excel, get data from one file and enter them into another new created file. I've created a folder Data and an excel data file [data.xlsx](https://github.com/G1ANT-Robot/G1ANT.Tutorials/blob/master/data.xlsx).

Firstly, we’re going to set a new variable equal to the path to the file in the computer because it is very useful. Variables are something like boxes where we store some types of information like numbers, letters or other characters.

Variables in G1ANT Language are followed by the heart sign and are displayed in green colour. To access this character either you can use keyboard shortcut Ctrl+4 or click *Menu/Insert* and choose it from the list.

We'll name this variable *datafile1*. The easiest way to get the path to a file is simply just open the file explorer and, in the folder, where our file is stored, copy the address of the folder which is here, at the top and add \name of the file and its extension to the whole address. The location of the file should be put in these *triple quotes*, the shortcut for this character is CTRL+'. 

```G1ANT
♥datafile1 = ‴C:\Users\a\Documents\G1ANT.Robot\Data\data.xlsx‴
```

We'll name the second excel file *data2.xlsx*. Even if it doesn't exist at the moment we can set the future existing path to a new variable *datafile2*.

```G1ANT
♥datafile2 = ‴C:\Users\a\Documents\G1ANT.Robot\Data\data2.xlsx‴
```

We'd like our robot to open *data.xlsx* therefore we use command **excel.open**.

```G1ANT
excel.open ♥datafile1
```

We've created *datafile1* variable so now it's time to use it instead pasting the whole address again in the path argument value.

```G1ANT
excel.getvalue row 1 colname a result ♥title1
```

To enter the same data in a new file, we should initially get G1ANT.Robot to remember them. It can be easily done by adding multiple **excel.getvalue** commands.

After **row** argument, we should put the name or the number of the cell's row that we want to get value from. After **colname** argument - the number or the name of the cell's column. You can also use **colindex** argument if you want to type the number of the cell without *triple quotes* which is not a string. The **result** argument lets us choose the name of the variable in which the value of the cell will be stored.

```G1ANT
dialog ♥title1
```

**dialog** command is often used when checking what in the variable is, this is the easiest way to get to know if Robot got the value from the cell.

Let's run it. As you can see, some pop-up window with the message *id* occurred. It means that G1ANT.Robot got value from this cell.

Let’s delete this line of code because it's no longer important in our automation.

Let's add more **excel.getvalue** commands so that we are able to enter all data from one row in data.xlsx into this new excel file.

```G1ANT
excel.getvalue row 1 colname b result ♥title2
excel.getvalue row 1 colname c result ♥title3
excel.getvalue row 1 colname d result ♥title4
excel.getvalue row 1 colname e result ♥title5
excel.getvalue row 1 colname f result ♥title6
```

Now we should open new excel workbook, so we type:

```G1ANT
excel.open
```

And now we are ready to set remembered values to the cells in the workbook. We'll need **excel.setvalue** command.

```G1ANT
excel.setvalue value ♥title1 row 1 colname a  
excel.setvalue value ♥title2 row 1 colname b  
excel.setvalue value ♥title3 row 1 colname c  
excel.setvalue value ♥title4 row 1 colname d  
excel.setvalue value ♥title5 row 1 colname e  
excel.setvalue value ♥title6 row 1 colname f  
```

We’re going to save this as *data2.xlsx* using **excel.save** command and run the script.

```G1ANT
excel.save ♥datafile2
```

Let’s save this script and check if in the specified location *data2.xlsx* file exist. It does! And it contains all the values from the first row.

**Whole code:**
```G1ANT
♥datafile1 = ‴C:\Users\a\Documents\G1ANT.Robot\Data\data.xlsx‴
♥datafile2 = ‴C:\Users\a\Documents\G1ANT.Robot\Data\data2.xlsx‴
excel.open ♥datafile1
excel.getvalue row 1 colname a result ♥title1
excel.getvalue row 1 colname b result ♥title2
excel.getvalue row 1 colname c result ♥title3
excel.getvalue row 1 colname d result ♥title4
excel.getvalue row 1 colname e result ♥title5
excel.getvalue row 1 colname f result ♥title6
excel.open
excel.setvalue value ♥title1 row 1 colname a  
excel.setvalue value ♥title2 row 1 colname b  
excel.setvalue value ♥title3 row 1 colname c  
excel.setvalue value ♥title4 row 1 colname d  
excel.setvalue value ♥title5 row 1 colname e  
excel.setvalue value ♥title6 row 1 colname f  
excel.save ♥datafile2
```
