
![](../../assets/Pasted%20image%2020260307230404.png)

This easy challenge as well 

we Start by downloading the image first 

![](../../assets/Pasted%20image%2020260307230756.png)
The file type of this picture is corrupted so it is not showing the actual file extension so essentially we should just fix few bytes to restore this.

If you check out the hints it says we should look the headers of the file and also the file type of this file is JPEG so all we have to do is to just correct the header to use the JPEG header and we can find that online. 

![](../../assets/Pasted%20image%2020260307231306.png)

any valid JPEG file should start with FFD8

First to check if even the marker is incorrect we can run xxd or hexdump 

![](../../assets/Pasted%20image%2020260307231518.png)

as you can see the first 4 digit is wrong since it starts as 5C 78 -> FF D8 then the file will be restored hence the flag.

we will using hexedit

![](../../assets/Pasted%20image%2020260307231823.png)

After we save the file we can open the file and see the flag.