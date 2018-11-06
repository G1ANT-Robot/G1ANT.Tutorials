# Lesson 2

The `keyboard` command you used in the previous lesson is not that primitive as you might think. Well, it is, considering the way it works, but these simple keyboard inputs are much more powerful when you start using keyboard shortcuts. Why? Because every program uses keyboard alternatives for its menus, tools and functions. You only need to find them and pass to your robot.

Let's go back to your simple Notepad robot. Its code looks like this:

```G1ANT
program notepad
keyboard Hello!⋘enter⋙‴I am robot.‴
```

Now you could use common Windows shortcuts such as **Ctrl+C** (copy to clipboard), **Ctrl+S** (save to a file) or **Alt+F4** (close program) to make the robot perform respective tasks. But Notepad allows you to do many other things: all of its tools are accessible with keyboard alternatives, which show up after pressing **Alt** key.

Run your robot by pressing **F9**. With Notepad open, you can investigate available keyboard options: press **Alt** key and look at the menu bar. First menu item, `File`, is depressed and all menu items have one letter in their names underlined. Now you can use arrow keys to navigate through menus or press the underlined letter to select a desired menu item. Fo example, if you wanted to activate word wrapping option, which is available in the `Format` menu, you would have to press **o** key (the underlined letter of the Format menu), then **w** in the dropped-down Format menu to select the `Word Wrap` item. The robot command sequence for these keystrokes would look like this:

```G1ANT
keyboard ⋘alt+o⋙w
```

Let's make something more powerful and robotized out of these keyboard inputs: select all notepad content and change its font size to 20. The keyboard shortcuts sequence would be:

1. Press **Alt+F** to open the `Format` menu.
2. Press **o** to select Font tool and bring out its dialog.
3. Press **Tab** twice to navigate to the font size box.
4. Enter the value of **20**.

The robot code would be as follows:

```G1ANT
keyboard ⋘alt+o⋙f⋘tab 2⋙20⋘enter⋙
```

You can use such combination of keyboard shortcuts and keystrokes to perform more advanced editing — for example, to find and replace some words or phrases. Say, you would want to change all instances of _robot_ in your Notepad text into _G1ANT.Robot_:

1. Bring up the Replace tool with **Ctrl+H**.
2. In Replace dialog, enter **robot** in the Find box and **G1ANT.Robot** in the Replace box.
3. Apply changes by pressing **Replace All** button.
4. Close the dialog with **Alt+F4**.

This translates into the following code in G1ANT.Robot language:

```G1ANT
keyboard ⋘ctrl+h⋙robot⋘tab⋙G1ANT.Robot⋘alt+a⋙⋘alt+f4⋙
```

After all operations, it would be nice to save changes to a text file named _robot.txt_ in a deafult location and close Notepad:

```G1ANT
keyboard ⋘ctrl+s⋙robot⋘enter⋙⋘alt+f4⋙
```

Now add the lines for changing the font, replacing words and saving a file to your first code:

```G1ANT
program notepad
keyboard Hello!⋘enter⋙‴I am robot.‴
keyboard ⋘alt+o⋙f⋘tab 2⋙20⋘enter⋙
keyboard ⋘ctrl+h⋙robot⋘tab⋙G1ANT.Robot⋘alt+a⋙⋘alt+f4⋙
keyboard ⋘ctrl+s⋙robot⋘enter⋙⋘alt+f4⋙
```

Run your robot with **F9** and enjoy its work.

In the next lesson you will learn how to make your robot repeat its operations.
