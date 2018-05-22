EXERCISES

Exercise 1
Using Robot:
1.	Open web browser
2.	Go to youtube.com
3.	Using javastript and robot get song name (it can be any song shown on the page)
4.	Display song name in a dialog window
5.	Close web browser

 
Exercise 2
Using robot and your favourite search engine look for “robotic process automation” 

Exercise 3
Create an excel and copy paste this list:

“LIST”
Using Robot:
1.	Open excel 
2.	Get the name of the first item
3.	Open web browser
4.	Go to amazon.com
5.	Search for item and then sort results by price from lowest
6.	Get the price of the cheapest item
7.	Save the price in excel in the second column
8.	Repeat for all items
Exercise 3 – the hard version
All that was in exercise 2 and:
1.	Add filtering by new item (new in options on left side)
2.	Look for results that fully comply with searched item, for example for item: “Lord of the Rings book” we won’t accept “Lord of the Rings Blu-ray”
3.	Discard all results with “Sponsored” label
4.	Create new exel file and save there 5 best results. Remember to take into consideration case where there are not enough results fulfilling given criteria. 
5.	Send an email with all the data
 
SAMPLE ANSWERS:

Exercise 1
```
selenium.open ‴chrome‴ url ‴youtube.com‴ 
selenium.runscript ‴return document.getElementById("video-title").innerText‴ result ♥songname errormessage ‴no song detected‴ 
dialog ‴Todays's song is: ♥songname‴ 
selenium.close
```

Exercise 2
```
selenium.open type ‴chrome‴ url ‴google.com‴
selenium.waitforvalue script ‴document.guerySelectorAll('#1st-ib').1ength > 0‴ expectedvalue ‴true‴
selenium.type text ‴robotic process automation‴ search ‴1st-ib‴ by ‴id‴ 
keyboard ⋘ENTER⋙
dialog ‴done‴
```

Exercise 3
```
xlsx.open ‴C:\Users\wikto\Documents\Book1.xlsx‴
♥row = 2
 
➜loop 
    xlsx.getvalue row ♥row colname a result ♥product 
    jump ➜end if ⊂♥product == ""⊃ 
dialog ‴Searching for: ♥product‴ 
    call ➤amazon 

    ♥row = ♥row + 1 
jump ➜loop
 
procedure ➤amazon 
    ie.open ‴www.amazon.com‴ 
    ie.runscript ‴document.getElementById('twotabsearchtextbox').value = '♥product'‴ 
    ie.runscript ‴document.getElementsByClassName('nav-input')[0].click()‴ 
    ie.waitforcomplete 10000 
    ie.runscript ‴location.href‴ result ♥url 
    ie.seturl ‴♥url&sort=price-asc-rank‴ timeout 10000 
    ie.runscript ‴document.getElementById('result_1').getElementsByClassName('a-link-normal s-access-detail-page s-color-twister-title-link a-text-normal')[0].title‴ result ♥itemname 
    ie.runscript ‴document.getElementById('result_1').getElementsByClassName('sx-price-whole')[0].innerText‴ result ♥pricewhole 
    ie.runscript ‴document.getElementsByClassName('sx-price-fractional')[0].innerText‴ result ♥pricefraction 
 
    dialog message ‴Found: ♥itemname with price: ♥pricewhole.♥pricefraction‴ 

    xlsx.setvalue value ♥itemname row ♥row colname b
    xlsx.setvalue value ♥pricewhole.♥pricefraction row ♥row colname c

    ie.close 
end 
 
 
➜end 
    dialog ‴All items processed!‴ 
    xlsx.close
```

