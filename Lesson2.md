Welcome to the second lesson!

In the previous one, we built a simple automation which could open G1ANT website for us. Let's come back to it and improve it a little. Click on the Task/Open because that is how you can find the previous script.

Let’s improve this automation which will also explore the G1ANT website so that we can just watch it, read it and do nothing else.

Before we start, please note that if your automation somehow doesn't work as you wished it to work (due to slow internet connection or a computer) or it is just too fast so it is hard to follow G1ANT.Robot steps, you can use **delay** command in the middle which stops the script for some seconds before it continues to the next line. The default value is 1 so we do not have to type **delay 1**, just writing **delay** will do the same (stop for one second).

We'll begin with mouse commands which simply manage mouse’s movements.

Not only can **mouse.click** perform right or left click but also press the mouse button for some time.

In order to scroll the whole website, we can get the position of the scroll bar on top and then at the bottom to perform the move of it.

Argument *button* lets us choose which mouse button will be pressed - left or right and argument *type* tells the computer whether it will be pressed (down) or just left not pressed (up).

```
mouse.click position ‴1430⫽115‴ button left type down
```

We get the position of the scroll at the bottom and it should look like this. Note that sometimes mouse action can be as quick that it will be necessary to slow it down as some website might not be able to get input due to not having loaded yet. Therefore **mousedelay** argument is needed which specifies time within a mouse should perform some action. Let's choose 1500 milliseconds for example.

```
mouse.click position ‴1429⫽780‴ button left type up mousedelay 1500
```

That is the end of this automation, it searched for G1ANT website using Internet Explorer and Google Search, opened it and explored so that the user could read it.

**Whole code:**
```
ie.open ‴google.com‴
window ‴Google - Internet Explorer‴
keyboard ⋘win+up⋙
keyboard ⋘f5⋙
keyboard G1ANT⋘enter⋙
mouse ‴144⫽214‴
mouse.click position ‴1430⫽115‴ button left type down
mouse.click position ‴1429⫽780‴ button left type up mousedelay 1500
```
