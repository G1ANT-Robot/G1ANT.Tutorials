Welcome to the third lesson!

This time we will automate excel, get data from one file and enter them into another new created file. I've created a folder Data and an excel data file *data.xlsx*.

Firstly, we’re going to set a new variable equal to the path to the file in the computer because it is very useful. Variables are something like boxes where we store some types of information like numbers, letters or other characters.

Variables in G1ANT Language are followed by the heart sign and are displayed in green colour. To access this character either you can use keyboard shortcut Ctrl+4 or click *Menu/Insert* and choose it from the list.

We'll name this variable *datafile1*. The easiest way to get the path to a file is simply just open the file explorer and, in the folder, where our file is stored, copy the address of the folder which is here, at the top and add \name of the file and its extension to the whole address. The location of the file should be put in these *triple quotes*, the shortcut for this character is CTRL+'. 

```
♥datafile1 = ‴C:\Users\a\Documents\G1ANT.Robot\Data\data.xlsx‴
```

We'll name the second excel file *data2.xlsx*. Even if it doesn't exist at the moment we can set the future existing path to a new variable *datafile2*.

```
♥datafile2 = ‴C:\Users\a\Documents\G1ANT.Robot\Data\data2.xlsx‴
```

We'd like our robot to open *data.xlsx* therefore we use command **excel.open**.

```
excel.open ♥datafile1
```

We've created *datafile1* variable so now it's time to use it instead pasting the whole address again in the path argument value.

```
excel.getvalue row 1 colname a result ♥title1
```

To enter the same data in a new file, we should initially get G1ANT.Robot to remember them. It can be easily done by adding multiple **excel.getvalue** commands.
