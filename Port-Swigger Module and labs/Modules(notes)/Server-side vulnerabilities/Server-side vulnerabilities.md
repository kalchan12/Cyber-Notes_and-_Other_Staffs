
# Path Traversal

## What is Path Traversal?

Path traversal (also called directory traversal) is basically when an attacker tricks a web application into accessing files it was never supposed to touch.

Normally, an app should only read files from a specific safe directory. But if the developer gets lazy (which happens a lot), user input gets directly used in file paths… and boom — now the attacker can start walking around the server’s file system like it’s their own house.

And yeah, it’s as bad as it sounds.

With this vulnerability, an attacker can:

- Read sensitive files (most common)
    
- Sometimes write or overwrite files (even worse)
    
- Potentially take full control of the server if things go really wrong
    

## Why this is dangerous (Impact)

This isn’t just “oh cool, I can read a file” — this can escalate fast.

An attacker might get access to:

- Application source code → now they understand how everything works
    
- Credentials → database passwords, API keys, etc.
    
- System files → like `/etc/passwd` on Linux
    
- Config files → which often contain secrets
    

If writing is possible:

- Modify app behavior
    
- Upload malicious scripts
    
- Gain remote code execution (game over)
    

## How it actually works (The core idea)

Let’s break it down with a simple example.

You’ve got a shopping website that shows product images:

```html
<img src="/loadImage?filename=218.png">
```

Seems harmless, right?

Behind the scenes, the server does something like this:

```
/var/www/images/ + filename
```

So if the user requests:

```
filename=218.png
```

The server reads:

```
/var/www/images/218.png
```

All good so far.

## Where things go wrong

The problem starts when the app blindly trusts user input.

An attacker can change the `filename` parameter like this:

```
../../../etc/passwd
```

So now the server builds this path:

```
/var/www/images/../../../etc/passwd
```

And here’s the trick:

`../` means “go up one directory”.

So:

- `/var/www/images/` → go up → `/var/www/`
    
- go up again → `/var/`
    
- go up again → `/`
    

Now we’re at the root of the filesystem.

Final result:

```
/etc/passwd
```

Congrats, the attacker just escaped the intended directory and accessed a system file.


## What is `/etc/passwd` and why should you care?

On Linux systems, `/etc/passwd` contains a list of all users on the system.

It’s not always super sensitive by itself, but:

- It confirms the vulnerability
    
- It helps attackers understand the system
    
- It’s often the first step before deeper attacks
    

Think of it like “Hello World” for path traversal.


## Windows version (same idea, different flavor)

Windows does the exact same thing, just with slightly different syntax.

Both of these work:

- `../`
    
- `..\`
    

Example attack:

```
..\..\..\windows\win.ini
```

So the attacker is now reading:

```
C:\windows\win.ini
```

Different OS, same mistake by the developer.


## Key takeaway (burn this into your brain)

If user input touches file paths without proper validation, it’s probably vulnerable.

And anytime you see something like:

- `file=`
    
- `filename=`
    
- `path=`
    
- `download=`
    

Your brain should immediately go:

“Can I try `../` here?”


## Quick mental model

Normal user:

```
/images/cat.png
```

Attacker:

```
/images/../../../etc/passwd
```

Same endpoint. Completely different outcome.



# Lab 1 : File path traversal, simple case

![](../../../assets/Pasted%20image%2020260408105902.png)

This is the first lab in this portswigger academy  series.


![](../../../assets/Pasted%20image%2020260408110440.png)

As i have discussed in my notes earlier this challenge is about file path traversal. which mean there are files (in our case images) are stored somewhere in the server that we can navigate to see what sensitive information are being stored without proper protection.

First we are going turn on foxy proxy or maybe use the built burp browser, if you don't wanna setup.

![](../../../assets/Pasted%20image%2020260408111524.png)

First turn on the intercept thou.
After opening the browser and refreshing it you will the fetched endpoints here.

The above screen shows that by default burp does not show images and other files so you should turn it on by clicking the Filter settings.


![](../../../assets/Pasted%20image%2020260408111817.png)

Next we should send the one of the images that starts filename.. to the repeater.

we first send it to the repeater can see this screen.

![](../../../assets/Pasted%20image%2020260408112152.png)

Next we will modify the payload to **/etc/passwd** 
- **/etc/passwd**  this command is used in linux OS or server to view someones password 
- for windows it looks like this **C:\windows\win.ini**

But this showed nothing because usually the etc password could be stored inside layered of directories so we should navigate till we reach the exact location where its stored

![](../../../assets/Pasted%20image%2020260408112520.png)

So we added ../../../ layers or this characters to help us navigate to the exact location where the credentials were stored.

As you can see it returned with the credentials we should not view hence path traversal Vulnerability.

![](../../../assets/Pasted%20image%2020260408112818.png)

As you can see the screen we have solved this lab!

## What is access control?


# Access Control

## Overview
Access control is about determining what actions a user is allowed to perform after they are authenticated.

## Core Concepts

- Authentication → verifies identity (who you are)
- Session Management → keeps track of the user across multiple HTTP requests
- Access Control (Authorization) → determines what actions the user can perform

## Important Concept: HTTP is Stateless

- Each request is independent
- Server does not remember users by default

## Sessions & Subsequent Requests

- After login, server creates a session
- A session ID is stored in a cookie
- Every request includes this session ID
- Server uses it to identify the user

## Security Impact

If session or access control is weak:
- Session hijacking
- Unauthorized actions
- Privilege escalation

## Key Takeaway
Authentication proves identity, sessions maintain identity, and access control enforces permissions.

## What is Vertical privilege escalation

This type of privilege escalation actually occurs when a regular user gains administrative rights hence can you operations like deleting other users accounts and more. 

## Unprotected functionality

in its basic form this type of privilege escalations occur when the application could not enforce protection sensitive functionality like administrative rights.

for example the website might host sensitive data in the following url.

`https://insecure-website.com/admin`

This shows that any other user can access it and often some other sensitive information might be stores this this common url. 

`https://insecure-website.com/robots.txt`

- `robots.txt` are one of the most common place to define what or what not to look on the website when the SEO tries to read or scrap the website. This might be good for website because it stops the SEO(Search Engines optimization) to not look into private data but it never stops humans thou. 
- Even if there is no information leaked inside the `robots.txt` there will always another option which is brute-force with crafted wordlists. 


## Lab 2 : Unprotected admin functionality

![](../../../assets/Pasted%20image%2020260430114806.png)

This Challenge describes that the lab have unprotected admin panel which implies that we can get vertical privilege escalation and perform whatever the admin could, in our case deleting user carlos.

The first thing to do is that to look in `robots.txt` url and as you can see the image down below we found a leak.
 - `Disallow: /administrator-panel` The Disallow command allows the SEO to not crawl the site but for human user it revealed something it should not be revealing which the admin page and there was role check every user just navigate at that url and go bananas. 

![](../../../assets/Pasted%20image%2020260430115140.png)

- as you can see down below once i navigated to the leaked url that i found in the `robots.txt`, i get to see the actual admin page which should not be possible if it was protected. 

![](../../../assets/Pasted%20image%2020260430115341.png)

- since our challenge was to delete carlos i did that and it worked and solved the challenge as you can see down below.

![](../../../assets/Pasted%20image%2020260430115559.png)

bye bye carlos 


