### CHALLENGE DESCRIPTION

Embark on the "Dimensional Escape Quest" where you wake up in a mysterious forest maze that's not quite of this world. Navigate singing squirrels, mischievous nymphs, and grumpy wizards in a whimsical labyrinth that may lead to otherworldly surprises. Will you conquer the enchanted maze or find yourself lost in a different dimension of magical challenges? The journey unfolds in this mystical escape!

### Category = Web
### Host add = 94.237.122.188:48324(unique for every user)

since we have our ip address we first put the Ip in our browser and see what is up.
![](../../assets/Pasted%20image%2020251124033421.png)
you will be greeted with this story like textual game.
to start the game you should type the start command.

once you do that you will see such screens. 

![](../../assets/Pasted%20image%2020251124033735.png)

Playing the game will not get you the flag so stop wasting your time because i have tried few options and said that is not the way to go.

So i opened up the dev tools which is always recommended right ?

![](../../assets/Pasted%20image%2020251124034059.png)

opened the Network section and there was nothing so i refreshed. 

![](../../assets/Pasted%20image%2020251124034235.png)

here we got some important files like 
- commands.js
- main.js
- game.js 
- option ( no extension so this was a sus)

I went through the java script files thinking i would find some hard coded flag or something to work with but boy was i wrong.

so finally i looked up the `options` file and i have found.

![](../../assets/Pasted%20image%2020251124034651.png)

I realized that there is a hidden secret key to get the flag which is shown above 

so the only to get the flag is to paste the secret key after starting the game 

![](../../assets/Pasted%20image%2020251124035159.png)

when you paste the secret key just like that you will get the flag. Good luck copy pasting the flag tho.