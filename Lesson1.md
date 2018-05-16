Hello, let's start learning how to code and do automations in G1ANT language.


Once you have G1ANT.Robot installed and opened, we are ready to do our first automation together. 

In the 1st tutorial we will automate searching G1ANT website using Internet Explorer browser and Google.

Let’s input the first line of our script:

```
ie.open ‴google.com‴ 
```

***Ie.open*** is a command, ***google.com*** is argument value. Arguments are placed in special characters. One of special characters is triple quotes, where we input text. To access Google website, we will input the weblink in triple quotes. We can do it in 2 ways: either by using shortcut CTRL+" or by clicking Insert and then choosing the character. Every character has its own shortcut. Shorts are accessible from the Insert within the Menu.

You can decide whether you’d like your automation to operate at the background or display the windows. To see the automation in action, we will use ***window*** command just like this:

```
window ‴Google - Internet Explorer‴	 
```

To bring a window to the front, we go to Tools/Windows (or shortcut Ctrl+W), copy the name of the window, select the program we would like to bring to the front, copy the name and paste it here within *triple quotes*.

Now, our Internet Explorer instance is brought to the front.

Let’s maximise our screen. We will input keyboard command and argument value. Using your keyboard, insert *triple angle brackets* (another special character type in G1ANT) which makes the robot use buttons to use a shortcut. Now type in win+up without spaces. 

```
keyboard ⋘win+up⋙
```

The quickest way to activate the cursor in search box, is to refresh the website by using F5. Let’s input ***keyboard*** command, *triple angle brackets* and type f5. 

```
keyboard ⋘f5⋙
```

G1ANT.Robot has built-in intellisense (or intelligent code completion), which makes you write the script faster. When you start typing command name a list of commands will appear which start with the letter you typed in, then by pressing enter, space button and a list of unique argument names for this command will appear, pressing enter and space buttons and special characters will appear. 

To search for G1ANT website, we need to type in G1ANT in Google search and type ENTER within *triple angle brackets* to press enter button. 

```
keyboard G1ANT⋘enter⋙
```

Let's launch the first part of the robot by either pressing the play button or simply by pressing F9 key on your keyboard. Now that the robot displayed the results, we can see that G1ANT website is at the top. And for the robot to click on the link, we need to use the mouse click command to get the position of the screen where the website is located. Input ***mouse.click*** command, then Insert and choose Mouse Position, say Yes to Absolute position (By the way, we choose absolute position, not relative to the active window). Now, using your mouse or mousepad navigate to G1ANT website and click on the link. As you can see, this has automatically inputted mouse position in your robot script. 

```
mouse.click ⟦point⟧144⫽214
```

Okay, we have just created our first robot using only 6 lines of script. Let’s press F9 or Play button to run the automation.

Let’s save our script for future use. We want to click Task/Save and call it Robot 1.  
