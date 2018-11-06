# Welcome to G1ANT.Robot Tutorials!

Since you are here, you are certainly aware of our robot's power. Here we will help you to unleash it easily, quickly and efficiently. Let's start robotizing!

The robot listens to your _commands_ — or rather reads them from the script editor. You can tell the robot to open a program, use a virtual keyboard or perform file operations, for example. All available commands are listed in the Commands pane (`View/Commands` menu), but you can also start typing and the editor will suggest you matching commands in a drop-down list of and provide a brief explanation of each one in a tooltip.

Type "p" and see what happens. From the resulting drop-down list, select `program`. This command tells the robot to run a program. When you select or type `program`, the robot will display another drop-down list with suggestions of _arguments_ — additional information needed to execute a given command. In case of the `program` command, the most obvious argument is a _name_ of the program to be launched by the robot. This name can be given in a short form such as **notepad**, **calc**, **chrome**, **word** (provided that these programs are installed in the system) or with a full path to the executable file, eg. **‴C:\Program Files\Internet Explorer\iexplore.exe‴** (note the triple prime character `‴` embracing the path — it's a special sign used in G1ANT.Robot for arguments containing spaces; to enter it, press **ctrl** and apostrophe **'** key).

Let's start with something simple like opening Windows Notepad and writing some text in it. In the script editor type:

```G1ANT
program notepad
```

Now press **F9** key or select Run from Debug menu. Notepad opens and waits for your input. Close notepad window for now.

Sending keyboard inputs to a program is easy and requires the `keyboard` command followed by the text to be entered or keyboard shortcuts/function keys to be mimicked by the robot. In this example, make the robot write:

**Hello!**

**I am robot.**

In the next line after your existing `program notepad` command, type:

```G1ANT
keyboard Hello!⋘enter⋙I am robot.
```

Did you notice `⋘enter⋙`? These triple quotation angles indicate a function key or a keyboard shortcut — **Enter** key in this example.

When you hit **F9**, you will see Notepad window with your text inside. Congrats, you've just created your first robot!

