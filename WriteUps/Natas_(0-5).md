## Natas | An [OverTheWire](https://overthewire.org/wargames/natas/natas0.html) game
---
Natas is a an [OverTheWire](https://overthewire.org/wargames/natas/natas0.html) game that teaches server side web security through hands on experience. Here is a Walk through of the levels 0-5 out of 34.

---
## Level 0

**You are given login credentials for the website and when opened are promted with this;**
<img width="1809" height="1231" alt="2025-11-08_13-20" src="https://github.com/user-attachments/assets/181c4791-aa02-40c1-9916-42e9789aaec9" />

**To find the password we can inspect the page for anything hidden**

<img width="2175" height="1246" alt="2025-11-08_13-20" src="https://github.com/user-attachments/assets/52d6e5a9-71cc-4ef7-a660-cd5d54205ffb" />


**Voila!**

---
## Level 1
**For the this level we use the username (given by OverTheWire) and the password we got before.**

<img width="2213" height="1228" alt="natas1" src="https://github.com/user-attachments/assets/00166310-f234-418d-9b02-e6d4f70ccf32" />

**As you can see we can use the same method as before for ths level**

---
## Level 2
**This is a bit different and introduces hidden directories.**

<img width="2235" height="1266" alt="natas2clue" src="https://github.com/user-attachments/assets/b84f644e-7a6d-4e30-b7da-ffedf5f53f3b" />

**As you can see after inspection we found something that catches our eye, a `[REDACTED]/` directory.**

**Using such information we know the website has another directory we might be able to access**.

**So we do *[Domain]* / `[REDACTED]` / in the search bar and we are prompted with this:**

<img width="376" height="81" alt="natas2found" src="https://github.com/user-attachments/assets/3954c3ec-7b0e-42df-b48a-18c1b88d4058" />

**And we get a hidden page:**

<img width="1447" height="1010" alt="natas2clue found" src="https://github.com/user-attachments/assets/f9143c9a-a4a1-47b2-8a00-b4bf27ee4755" />

**"`users.txt`" is a bit tempting to open isnt it? :)**

**Lets see whats inside:**

 `[REDACTED]` `[REDACTED]` `[REDACTED]` `[REDACTED]` `[REDACTED]` `[REDACTED]` `[REDACTED]` `[REDACTED]` `[REDACTED]` `[REDACTED]` `[REDACTED]` `[REDACTED]` `[REDACTED]` `[REDACTED]`  `[REDACTED]` `[REDACTED]` `[REDACTED]` `[REDACTED]` `[REDACTED]` `[REDACTED]`

***DO IT YOUR SELF!!!***

**Opening `users.txt` will reveal the password to the next level**

---
## Level 3
**After using the previously found credential we advance to level 3**

<img width="2067" height="1269" alt="natas3clue" src="https://github.com/user-attachments/assets/7d8e4729-56fd-42f7-8daf-a1401e1ab567" />

**We can see that there is no usefull data in here however there seems to be a hint**

<img width="904" height="51" alt="image" src="https://github.com/user-attachments/assets/0e698b36-5c88-4011-80b0-743616f46304" />

**`Google` might hint something related to [*webcrawlers*](https://en.wikipedia.org/wiki/Web_crawler). We can know that they usually index files related to a website but we didnt find any here.**

**So is it a dead end?...**

**Nope! Usually Google allows site owners to select if certian files or directories can be indexed by the webcrawler. Such settings are usually stored in `robots.txt`**

**So if we add `robots.txt` at the end of the domain:**

<img width="407" height="211" alt="natas3clue2" src="https://github.com/user-attachments/assets/538d7fe1-02e7-4995-8924-6181e64f5cf7" />

**We get something like this:**

<img width="822" height="498" alt="NATAS3 SECERET DIRECTORY " src="https://github.com/user-attachments/assets/87772450-8df1-4479-a46d-df6a3c33f088" />

**Now we know about a directoy called `/[REDACTED]/`. Lets take a look!**

<img width="1336" height="635" alt="natas3found" src="https://github.com/user-attachments/assets/da0a1211-dab5-4a59-bcf3-ab593214c3f4" />

**Voila!**

---

## Level 4 
**This level requires a new tool as it introduces a new concept.** 

<img width="1344" height="1065" alt="natas4clue" src="https://github.com/user-attachments/assets/b22bf35e-a70c-4bac-a496-54451813efa1" />

**The `Refresh page` button indicates that the website we are on might send a request to the server to check what we are visiting from. In our case we don't seem to be meeting the requirement as mentioned.**

**How can one just intercept these requests and maybe change them; pretending to be someone else...?**

**To do this, we can use Burp Suite** 

<img width="300" height="104" alt="image" src="https://github.com/user-attachments/assets/7811a6e7-f20f-4e00-b1e3-8f88b4b60a03" />

**We open a new temporary project and launch Burp's Chrome like browser.**
**After clearing the initail logs we will enter are url in the browser then go to the *Proxy* tab and *turn intercept on*. Now we will refresh the page and burp will intercept the request as if its a car stopped in a checkpost. Now we can see some details**

<img width="2217" height="1331" alt="nats4 solved" src="https://github.com/user-attachments/assets/9dc00ebb-9389-4f79-935f-de0a04b94be9" />

**We can just changed the referer (whos sending the request) and pretended to be the authorized user and *forward*ed the request.**

**Simple!**

---
## Level 5

**We are prompted with this:**

<img width="1149" height="500" alt="natas5clue" src="https://github.com/user-attachments/assets/db41c12c-4995-46df-9276-2aca2c612aef" />

**Again we can tell that its using some sort of check which will have to send a request to the server to verify if we are `logged in`**

**When ispecting the request in Burp Suite like before we see this:**

<img width="1699" height="1094" alt="natas5cluesolver" src="https://github.com/user-attachments/assets/a80b4947-44ff-4531-9d1f-db85b4415ed3" />

**Usualy `0` means Off, no, etc and `1` means On, yes, etc. so as mentioned before that we arent logged in we can change this [Cookie](https://en.wikipedia.org/wiki/HTTP_cookie): `loggedin-[0]`to `loggedin-[1]`**

**Then we see this:**

<img width="1088" height="617" alt="natas5 solved" src="https://github.com/user-attachments/assets/0c3925fe-1bef-4782-8d0c-6e949c7aef0c" />

**Easy!**

---

## Reflections
Some of the important things I learned after working through these Natas levels was that web security doesn't have to involve complex exploits or fancy hacking tools. Most vulnerabilities boil down to simple mistakes: leaving sensitive data in HTML comments, exposing directory listings, forgetting about robots.txt, or trusting client-side data like cookies and referrer headers.

It felt like a natural progression: each level built upon the last, starting with simple HTML inspection and moving into how HTTP requests work. By the time I got to level 4, I wasn't just looking at what was visible on a page anymore; I was thinking about the communication between my browser and the server and realizing just how easy it is to manipulate that conversation.
Burp Suite was a game changer. Up until then, HTTP headers and cookies were abstract concepts. The idea of being able to see them in real time and actually pausing requests midflight to modify them made everything click. It's one thing to read that cookies can be tampered with; it's another to actually change "loggedin=0" to "loggedin=1" and watch the server just accept it.
What surprised me most was how much security relies on obscurity rather than actual protection. Hidden directories, robots.txt files listing exactly what shouldn't be found, cookies that control access without any server-side verification—these aren't secure; they're just hoping nobody looks too closely.

These early levels weren't technically hard, but it flipped something in my brain about how to think about websites. Every page I go to now, I think: What's in the source code? What directories are there? What does my browser tell the server about me? It made me realize that security isn't some separate layer you add on—it has to be baked into every decision from the start.

---
> ريان عبدالله خان














