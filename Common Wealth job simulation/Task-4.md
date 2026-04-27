Task 4 : Penetration testing
         Task Overview
     What you'll learn
        - Gain understanding of penetration testing principles and techniques.
        - Learn to identify and exploit vulnerabilities in web applications.    
        - Understand the importance of creating a comprehensive penetration testing report.
    What you'll do
        - Create an account on HackThisSite and complete all 11 levels of the "Basic" web challenge.
        - Document a Penetration Testing Report including an executive summary, scope, vulnerability descriptions, key findings, and security recommendations for each level.
        - Apply the knowledge gained from the challenge to real-world scenarios and improve penetration testing skills.
basic 1 
![[Screenshot 2026-04-15 155254.png]]

Using the hint  right click the page and view page source and scroll down(browser-specific)

![[Screenshot 2026-04-15 155212.png]]

The password is d2cdad20

![[Screenshot 2026-04-15 155322.png]]

Basic 2
After staring at the source code for 30 mins, and found no password , like in basic 1 concluded that there was no password needed. so i just hit enter and yes , that was the solution.

![[Pasted image 20260422162238.png]]

Basic 3 
upon inspecting the source code , the password.php file which is a webpage
so i entered that in the url
 
 https://www.hackthissite.org/missions/basic/3/password.php

![[Pasted image 20260422162538.png]]

and it revealed a page with the password. and that is the ans

Ans : 045ed82f

![[Pasted image 20260422163155.png]]

basic 4

![[Pasted image 20260422163605.png]]

After testing the send password to sam button , a page appears that saying that the password was sent to sam@hackthissite.org , i then decide to inspect the page

![[Pasted image 20260422164124.png]]

then locating the button function i change the email to mine (and you must use the actual email you registered) also the name for flare.

![[Pasted image 20260422165857.png]]

then hit the send button.

![[Pasted image 20260422170052.png]]

Then i checked my mail and i saw the password.

![[Pasted image 20260422170238.png]]

Answer : 7375ebbf

![[Pasted image 20260422170348.png]]

Basic 5

literally repeat the same steps as basic 4

Answer : 370dc3ae

![[Pasted image 20260422172715.png]]

basic  6 

![[Pasted image 20260422175332.png]]

 the question mention encrypting , and ask we enter a string which i did , i entered "sam" and the ciphertext was "sbo" , this was a clue, i you observe closely the 
 
 S  = S
 A = B
 M = O

looking closely one can tell the what happened to the ciphertext and how the Encryption algorithm works , it works  with an incremental shift cipher.

Encrypted a test text

| Cipher      | 0   | 1   | 2   |
| ----------- | --- | --- | --- |
| Plain text  | S   | A   | M   |
| Cipher text | S   | B   | O   |
refer to the alphabet table for better understanding. but this is just half of it, looking back at the question the cipher of sam's password is already given **f18:<h8;**  and last i checked the alphabet table does not have not numbers and special characters but the ASCII table does so using the table

Decrypting the cipher text

| Cipher      | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   |
| ----------- | --- | --- | --- | --- | --- | --- | --- | --- |
| cipher text | f   | 1   | 8   | :   | <   | h   | 8   | ;   |
| plain text  | f   | 0   | 6   | 7   | 8   | c   | 2   | 4   |
refer to the ASCII for clarity https://www.asciitable.com/

Answer : f0678c24

![[Pasted image 20260422175305.png]]

Basic 7
![[Pasted image 20260422181719.png]]

for this  level 7, i ran the cal command and a blank screen , then i entered a year and i revealed the output that contains  a complete calendar of the year  i entered like so
![[Pasted image 20260422212537.png]]

yes i entered the year 40k , but something was still off,  the scenario states that the password is stored  this is directory , so i tried using Dir commands like ls, pwd, cd all of which still displayed a with screen.
So only the cal function is working, then i tried command chaining like so 

2000 ; ls 

and that did it .

![[Pasted image 20260422213119.png]]

Then enter the .php file into the url bar 

 https://www.hackthissite.org/missions/basic/7/k1kh31b1n55h.php

This reveal the answer

Answer : 78e69f7c
![[Pasted image 20260422213259.png]]
Lesson learned.
The reason command injection works is because the developer **never sanitized the input** — they trusted whatever the user typed and passed it straight to the shell.

Basic 8
![[Pasted image 20260422225730.png]]

I researched more about how to script SSI commands and found [this](https://www.w3.org/Jigsaw/Doc/User/SSI.html#exec). `<!--#exec cmd="ls -lsa" -->` didn't quite work either, but I got a message telling me I was on the right track.

`<!--#exec cmd="ls" -->` listed a bunch of .shtml files in the output. More progress! But I realized the resulting URL was for
![[Pasted image 20260422230119.png]]
[[https://www.hackthissite.org/missions/basic/8/tmp/ugpsnhtj.shtml](https://www.hackthissite.org/missions/basic/8/tmp/ugpsnhtj.shtml)](https://www.hackthissite.org/missions/basic/8/tmp/jnesyski.shtml). I was one directory up, according to the scenario , since I wanted to be in [https://www.hackthissite.org/missions/basic/8/](https://www.hackthissite.org/missions/basic/8/) per the mission instructions. 

So, `<!--#exec cmd="ls ../" -->` moved me back up a level in the directory tree and listed the contents there, revealing the name of a PHP file – in my case it was au12ha39vc.php. 
![[Pasted image 20260422230408.png]]
Navigating to [https://www.hackthissite.org/missions/basic/8/au12ha39vc.php](https://www.hackthissite.org/missions/basic/8/au12ha39vc.php) gave me my answer.
![[Pasted image 20260422230702.png]]
Answer : 2c1a6ca5


Basic 9 

![[Pasted image 20260422230942.png]]

The mission description suggests the vulnerabiilty from Mission 8 is still in play, even though there's no input box for this mission. So we still want to list directory contents, but this time for directory /9/. So, let's go back to Mission 8 and enter this into the script input box: `<!--#exec cmd="ls ../../9/" -->`. This allows you to change directories over to /9/, revealing the name of the PHP file allowing you to find the password similar to what you did in Mission 8.

![[Pasted image 20260422231043.png]]
Answer ;  1f787a16

basic 10

Take note of the hint about JavaScript. If you open Developer Tools, try printing the value of document.cookie from the Console. For me it looked something like `level10_authorized=no; PHPSESSID={session ID value}`. What if we changed the value so `level10_authorized=yes`?

You can do this in a variety of ways. The manual way would be to simply enter `document.cookie="level10_authorized=yes";` into the Console and run it. You can also use the JavaScript alert() function to view and modify the cookie contents, as seen [here](http://www.testingsecurity.com/how-to-test/injection-vulnerabilities/Javascript-Injection).

basic 11
Not understanding Apache is a clue, because directory listing in Apache is often [enabled by default](https://www.techrepublic.com/article/how-to-make-apache-more-secure-by-hiding-directory-folders/). This means a user can map out subdirectories of your site if he or she successfully enters in a URL which resolves to a directory path.

When you load the mission, text like 'I love my music! "Georgia " is the best!' appears. If you referesh the page, a new song appears in the text. All of these are songs by Elton John. Given that we know directory listing is probably enabled, try navigating to some URL structures to see if they work. [https://www.hackthissite.org/missions/basic/11/a/](https://www.hackthissite.org/missions/basic/11/a/), [https://www.hackthissite.org/missions/basic/11/b/](https://www.hackthissite.org/missions/basic/11/b/), etc.

Eventually [https://www.hackthissite.org/missions/basic/11/e/](https://www.hackthissite.org/missions/basic/11/e/) works. Click through the ensuing directories you discover and you'll end up at [https://www.hackthissite.org/missions/basic/11/e/l/t/o/n/](https://www.hackthissite.org/missions/basic/11/e/l/t/o/n/). This directory seems empty, but try accessing the .htaccess file at [https://www.hackthissite.org/missions/basic/11/e/l/t/o/n/.htaccess](https://www.hackthissite.org/missions/basic/11/e/l/t/o/n/.htaccess).

The .htaccess file loads, revealing these contents:

```
IndexIgnore DaAnswer.* .htaccess
<Files .htaccess>
require all granted
</Files>
```

Navigate to [https://www.hackthissite.org/missions/basic/11/e/l/t/o/n/DaAnswer/](https://www.hackthissite.org/missions/basic/11/e/l/t/o/n/DaAnswer/). I saw something like this: 'The answer is not here! Just look a little harder.'

Now navigate to [https://www.hackthissite.org/missions/basic/11/index.php](https://www.hackthissite.org/missions/basic/11/index.php), enter 'not here' as your password (or whatever the text changes to if the text you see is different), click through, click Go On, and you're done.
