![](../../assets/Pasted%20image%2020260307222453.png)

This Challenge is easy but tricky 

we first start by downloading the image by clicking the link. 

The first to do in this kinda challenge is to see the metadata of the image. 

![](../../assets/Pasted%20image%2020260307222825.png)


we usually use exiftool to see the metadata and it is a solid tool.

from this metadata the only interesting information is the comment section because it might be encoded text and it looks like base 64 encoding so we can decode using tools like cyberchef https://gchq.github.io/CyberChef/ and there many but i will be using the terminal.


![](../../assets/Pasted%20image%2020260307223401.png)

The first encoded string gave me another base 64 string and which gave readable text = pAzzword.
at this point i thought this was the flag and i put it into picCTF{pAzzword} format but it was not over.

If you noticed the first base64 when decoded yield `steghide : cEF6endvcmQ=` the important stuff here is the hint about steghide because steghide is a tool to embed stuff in image. 

Finally you can run this command `steghide extract -sf img.jpg -p pAzzword` in the terminal 

you will something like this 

![](../../assets/Pasted%20image%2020260307224240.png)

after that you will just cat the text out then you shall see the flag.