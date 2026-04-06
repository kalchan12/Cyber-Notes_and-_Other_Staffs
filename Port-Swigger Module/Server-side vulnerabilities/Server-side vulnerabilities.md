Alright, this is a solid start — you’ve got the right idea, just needs cleanup, better flow, and some “future-you-at-2AM” clarity. I’m gonna rewrite it so it actually _sticks in your brain_.

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
