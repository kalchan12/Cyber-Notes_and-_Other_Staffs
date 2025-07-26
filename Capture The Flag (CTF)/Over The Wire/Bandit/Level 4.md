![](../../../assets/Pasted%20image%2020250726160053.png)

In this Challenge the password is still in the same directory but there are many files and most of them are not human readable file except for one. We will how we automate that 

![](../../../assets/Pasted%20image%2020250726213436.png)

### Challenge:

> The password is stored in the **only human-readable file** inside the `inhere` directory. You're supposed to find and read it  but not by manually guessing each one.

---

### ✅ Step-by-step Explanation


`cd inhere`

🔹 You enter the `inhere` directory where all the mysterious files are stored.

---

`ls`

🔹 Lists all the files. You get:


`-file00  -file01  -file02  ...  -file09`

🧠 All filenames start with a dash `-`, which can cause issues because commands think you're passing options (like `-l`, `-a`, etc).

---

`cat ./-file00`

🔹 You attempt to read one file using `cat`, but it spits out gibberish:

**`ŉOTS plS]-EHt:-Z`**

💡 This tells you it's not human-readable.

---


`file ./*`

🔹 This is the **key move**. The `file` command analyzes the contents of each file and tells you what type it is:

Output:

`./-file00: PGP Secret Sub-key - ./-file01: data ... ./-file07: ASCII text`

🧠 Only `./-file07` is **ASCII text**, which means it’s human-readable. That’s your target.

---

`cat ./-file07`

🔹 You read the file that `file` told you is readable, and BOOM:

🎯 That’s the **password** for the next level (Bandit 5).

---

### ⚙️ Why These Commands Work:

|Command|Purpose|
|---|---|
|`cd inhere`|Move into the folder with the hidden file|
|`ls`|See all available files|
|`file ./*`|Analyze each file’s content type|
|`cat ./-file07`|Safely read the human-readable file (use `./` to avoid issues with `-`)|