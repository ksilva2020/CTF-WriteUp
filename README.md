# CTF-WriteUp

##CTF  5.08 Colombia 

CTF challenge testing competitor’s skills on IDOR (Insecure Direct Object Reference). 

###Hints

The main page gives us hints that we should look for a piece of information that will give away even more information that we are not supposed to see. 


- IDOR

- Cypher using to encode Hebrew alphabet
- 
- There is a link that takes us to the page where we will work on. Another hint
- Exclamation point 

-The exclamation mark is one space distant from the last word. Leading us to think of investigating the element page and  to see if we can introduce something between the word and the exclamation mark (after “User” and before “!”).  

###Plan of Attack

We decide to try various inputs and think numbers are the best bet.                             
We manipulated the URL by adding “?id= “ at the end.                                                
Random numbers kept the page up, which told us this is what should be manipulated. 
Using the Intruder feature on BURP we insert  a lot of numbers (from 1 - 30) in the URL, which puts them between  “Welcome User” and before the “!”                                               
User number 24 had the  password shown *XGU{ZIILTZMG_TVMGOVNZM_WVNLM} which according to the hint needs to be deciphered as an ATBASH (ancient substitute cipher used to encode the Hebrew alphabet).                                                                      
On Burp Suite I launch an Intruder Attack the test numbers. Number 24 shows letter in the flag format: (*XGU{ZIILTZMG_TVMGOVNZM_WVNLM} 
The hint on the initial page says something about a monoalphabetic substitution cipher originally used to encrypt the Hebrew alphabet” which after an internet search comes back as ATBASH. I put the jumble phrase in Cipher decoder and get the flag: *CTF{ARROGANT_GENTLEMAN_DEMON}.          

###Conclusion

Knowing beforehand this was an IDOR challenge helped me focus on trying to find  a piece of information that would be exposed,or blatantly missing. The hint about the ancient cipher was helpful toward the end, although not much because the Cipher decoder picked up on what it was instantly. 

###Tools and resources: 

-https://ctf.codepath.com/index.php?p=game

-https://flags.codepath.com/http/public/protected/flags/crypto_idor/

-Burp Suite

-https://www.dcode.fr/cipher-identifier




