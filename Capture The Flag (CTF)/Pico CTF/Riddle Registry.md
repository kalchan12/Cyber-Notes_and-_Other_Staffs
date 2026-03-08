
![](../../assets/Pasted%20image%2020260308213719.png)

This challenge is on easy category but it was tricky for me because i went in totally different direction and if i only used the hints that are been given. 

The hint basically suggest to look for metadata instead extracting anything which i have been doing. 

# My Mistakes 

**First step** 

![](../../assets/Screenshot%20From%202026-03-08%2018-37-32.png)

I ran strings with different options. This was actually not a bad move but it just was not good one in our case. 

**Second Step** 

I tried to view the pdf maybe the redacted files can be uncovered when pasted on other notepad (Epistien mode) but that was not working. 

![](../../assets/Screenshot%20From%202026-03-08%2018-42-36.png)

**Third Step**

Then i used one the tools i know to extract whatever hidden there. 

`pdftotext confidential.pdf` i ran this command. 

it extracted confidential.txt file and i hoped i could get the flag but there was nothing but a decoy. 

![](../../assets/Screenshot%20From%202026-03-08%2018-47-17.png)

It was this moment i know i fucked up 


# The real why of solving this 

**First step**

Get the metadata and there are many tools to do so but i will using the infamous exiftool.

![](../../assets/Screenshot%20From%202026-03-08%2018-50-17.png)

One thing i realized here in this metadata is that there a base64 encoding there under author row.

**Second step** 

Decoding this 

I used the terminal but there are many ways. 

![](../../assets/Screenshot%20From%202026-03-08%2018-53-28.png)

and then this is it. It was this easy only took me 2 steps. 