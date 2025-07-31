![](../../../assets/Pasted%20image%2020250731101419.png)

This Challenge Deals with a lot about compression
Our task involves is Identifying the file type and and compress or decompress accordingly. 

![](../../../assets/Pasted%20image%2020250731101535.png)

# 📁 Creating a Temp Folder (The Smart Way)

When working on CTFs (like Bandit Level 12), you’ll often deal with files that are **compressed multiple times**. Instead of messing up your home directory, create a **temporary working folder**.

---

## ✅ The Right Way:

`WORKDIR=$(mktemp -d) cd "$WORKDIR"`

### 🔍 What it does:

- `mktemp -d`: Creates a secure, random temp folder in `/tmp`
    
- `WORKDIR=$(...)`: Saves that path in a variable
    
- `cd "$WORKDIR"`: Moves you into it
    

Now you’ve got a **private, disposable workspace**.

---

## ❌ The Wrong Way:

`mkdir /tmp/myfolder cd /tmp/myfolder`

This works, but:

- It’s **predictable**
    
- Might cause **name conflicts**
    
- Not safe in **shared environments**
    

---

## 🧹 Clean Up:

When you're done, just nuke the whole thing:


`rm -rf "$WORKDIR"`

---

## ⚡ Summary:

Use `mktemp -d` + `WORKDIR` for safe, clean, and script-friendly temp work.

> Pro move for CTFs, automation, and not leaving a mess behind. 💻💣


![](../../../assets/Pasted%20image%2020250731101805.png)
Lets break down this commands 

 - First we will `ls` to list the directory and as it is shown in the above image we got data.txt 
 - `Cp data.txt "&WORKDIR` this command will copy the file into the temp folder we created 
 -  `CD  "&WORKDIR" this will change the directory into the temp directory where we copied our file.
 

![](../../../assets/Pasted%20image%2020250731102244.png)

- Second Step would be just simply watching what type of file it's since this all about compressed files 
- we can view the file type with the ` File` command 
- `file data.txt` will show us that it is file type. In our case the file type is **ASCII Text** 

![](../../../assets/Pasted%20image%2020250731102314.png)


- Since it is a text file type we used 
   `cat data.txt`
   but the text is not human readable text it is hex dumb 

![](../../../assets/Pasted%20image%2020250731102745.png)

- xxd -r data.txt data.bin
    xxd -r: undoes the hexdump (hex → binary)
    data.bin: new binary file created
- we can see we got new new file called `data.bin  
 -  so from now on we going to read the file type and decompress it 

### 🔁 Rename & Decompress Layer by Layer

Now use what the `file` command tells you:

#### Example 1: If it's gzip

`mv data.bin file.gz`  = Moves(Renames) the file into .gz file
`gunzip file.gz` = Decompress the file after it is renamed into .gz file

#### Example 2: If it's bzip2

`mv file file.bz2 ` = Moves(Renames) the file into .bz2 file
`bzip2 -d file.bz2` = Decompress the file after it is renamed into .bz2 file


#### Example 3: If it’s a tar file

`mv file file.tar `  Moves(Renames) the file into .tar file
`tar -xf file.tar` = Decompress the file after it is renamed into .tar file


### 🔄 Repeat:

- Use `file` to check the new file type
    
- Rename it if needed
    
- Decompress
    
- Repeat until you get readable text


![](../../../assets/Pasted%20image%2020250731103543.png)


![](../../../assets/Pasted%20image%2020250731104049.png)
- You might see that the file is getting named like **File, File2, File3**
  but this is just me being lazy but you can rename it however you like it.

![](../../../assets/Pasted%20image%2020250731104854.png)

After running the necessary commands, we finally extracted an ASCII text file containing the password.



## 🧠 Final Thoughts

In a real-world scenario, we’d absolutely automate this entire process using a **Bash** or **Python** script. It would handle file detection, decompression, and even cleanup — saving us time and effort, especially when dealing with layered files or repetitive tasks.

But since we’re working inside the **Bandit CTF environment**, we’re restricted — no script execution, no write access in home directories, and limited tools.

So, we roll old-school — **one command at a time**, learning how each one works. And honestly? That’s the point. It forces you to understand the Linux toolbox before relying on automation.

> We _could_ script it in the real world, but here, we _learn_ by grinding it out. 🧠💻🔥


```bash
#!/bin/bash

# Create a secure temp working directory
WORKDIR=$(mktemp -d)
echo "[+] Working in $WORKDIR"
cd "$WORKDIR" || exit

# Copy the original hexdump file (make sure to run from the correct dir)
cp ~/data.txt .

# Reverse the hexdump to binary
xxd -r data.txt file

# Loop: identify and decompress until it's plain text
while true; do
    FILETYPE=$(file file)
    echo "[*] Detected: $FILETYPE"

    if echo "$FILETYPE" | grep -q "ASCII text"; then
        echo "[+] Final Output:"
        cat file
        break
    elif echo "$FILETYPE" | grep -q "gzip compressed"; then
        mv file file.gz && gunzip file.gz
    elif echo "$FILETYPE" | grep -q "bzip2 compressed"; then
        mv file file.bz2 && bzip2 -d file.bz2
    elif echo "$FILETYPE" | grep -q "POSIX tar archive"; then
        mv file file.tar && tar -xf file.tar && FILE=$(ls) && mv "$FILE" file
    else
        echo "[!] Unknown format. Exiting."
        break
    fi
done

# Optional: cleanup
# rm -rf "$WORKDIR"
```
