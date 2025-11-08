## Natas | An [OverTheWire](https://overthewire.org/wargames/natas/natas0.html) game
---
Natas is a an [OverTheWire](https://overthewire.org/wargames/natas/natas0.html) game that teaches server side web security through hands on experience. Here is a Walk through of the levels 0-5 out of 34.

---
## Level 0

**You are given login credentials for the website and when opened are promted with this;**
<img width="1809" height="1231" alt="2025-11-08_13-20" src="https://github.com/user-attachments/assets/181c4791-aa02-40c1-9916-42e9789aaec9" />

**To find the password we can inspect the page for anything hidden**





<img width="2175" height="1246" alt="nats0answer" src="https://github.com/user-attachments/assets/ad3a59dc-8e44-4263-af3d-8d3cb1b2cf91" />

**Voila!**

---
## Level 1
**For the this level we use the username (given by OverTheWire) and the password we got before.**

<img width="2213" height="1228" alt="natas1" src="https://github.com/user-attachments/assets/b574868a-68af-4fde-9b1a-f6d730912f43" />

**As you can see we can use the same method as before for ths level**

---
## Level 2
**This is a bit different and introduces hidden directories.**

<img width="2235" height="1266" alt="natas2clue" src="https://github.com/user-attachments/assets/49d77de7-135e-465d-bc3f-dce6e20e6101" />

**As you can see after inspection we found something that catches our eye, a `files/` directory.**

**Using such information we know the website has another directory we might be able to access**.

**So we do *[Domain]* / `files` / in the search bar and we are prompted with this:**

<img width="376" height="81" alt="natas2clue2" src="https://github.com/user-attachments/assets/da2b0d04-461f-470b-879a-e8fb14a5b5b3" />

**And we get a hidden paged:**


<img width="1447" height="1010" alt="natas2clue found" src="https://github.com/user-attachments/assets/da908546-8563-4664-a23f-ebc1285447b1" />

**"`users.txt`" is a bit tempting to open isnt it? :)**

**Lets see whats inside:**

<img width="1055" height="498" alt="natas2found" src="https://github.com/user-attachments/assets/86030e59-b3cc-43b3-bbcd-408eb927ae41" />

**As you can see, we have found a user list with passwords by simply finding vunerabilities on the website.**

---
## Level 3
**After using the previously found credential we advance to level 3**

<img width="2067" height="1269" alt="natas3clue" src="https://github.com/user-attachments/assets/7d8e4729-56fd-42f7-8daf-a1401e1ab567" />

**We can see that there is no usefull data in here however there seems to be a hint**

<img width="904" height="51" alt="image" src="https://github.com/user-attachments/assets/0e698b36-5c88-4011-80b0-743616f46304" />

**`Google` might hint something related to [*webcrawlers*](https://en.wikipedia.org/wiki/Web_crawler).**





