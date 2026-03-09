![](../../assets/Pasted%20image%2020260309150331.png)

If you check the hints it suggests to use grep which makes the challenge more like cryptography. This challenge teaches the beginner how to use grep which is very important tool to search through textual files.

**First Step**

![](../../assets/Pasted%20image%2020260309151059.png)

when we run `grep` to filter with `picoCTF` since it is the flag format for pico ctf and it came with parts of the flag but it was not the whole flag so this where we should use different argument. 

One thing we notice here is that, `FLAGPART :` is very common or it is more frequent word so we will be filtering by that.

![](../../assets/Pasted%20image%2020260309151612.png)

You can literally assemble the flags all together by looking at the order and ignoring the duplicates or you can run this command 

```
grep FLAGPART server.log | awk -F'FLAGPART: ' '!seen[$2]++ {print $2}' | tr -d '\n'

```

The flag is already in the screenshot but the above command is slick way to automate it 
