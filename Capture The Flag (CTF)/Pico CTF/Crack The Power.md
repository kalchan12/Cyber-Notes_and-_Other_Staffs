
![](../../assets/Pasted%20image%2020260309155408.png)

This problem was kinda of hard for me and i had to research and learn more about Coppersmith to kinda reverse engineer i guess. 

**First Step**

Open up the file to see what's up

```
n = 592325447231738441351071489581088757233720739925609258047099666430012235601850645552329901005075391294293223406036889957923559576128331131378606442742236488270084671950952525799667698301888056635664647656977243955217676947680067343522830281673120964015865084297057562151985539484574606861778569266488009140494364134935594914464890031028626938636135840340989506946742101548151422852165141296441876615643237931476602730416257898139870754749380043234067453918829041163045563911664548932389849819848844526231000350277208242446525723712715055346442058050630332320809321659096291341949060568006445905152077621745995275679882352413969031178227940209082465512704189115382281267388968000345389442569760325080529555465995924905321941388567353294157787055153832603281012811165235055220934957378947120291762452509894348538378268314496253843977368080389012784966563661851973054126590176691159451419543381120937484358594961085858997671262313801439268789843279148461058409883556649656815050562373027948928859890413154749488107217200550454373275296933326911207985807494373758474833112011249505201812056343685582853686546861380734925735510740317008680993783259119425204236762139101843967235368549189165369156547430089151157933732839704498166715989411
e = 20
c = 640637430810406857500566702096274083827969484683203431057884917289334852774628366544173898461793872749381218755789561147579616430654545910443392999745646991166871881921220464939864253713908416530390190158949384932577913862830219713857369609459762011889417419756793122426703825117513400191620385907288504916090847305768659601562703145161353515226108384753106940659543471151834612884216177615674237258524708660356029782277496502661375640482568436495365098768844463148890142800375234779194361829383863910733638511522447466825092214583332860815273048698909839939639414519049464503518148811430663951050780377349263954109578307275120668187576579606920834997300457959369210342979008781474779797263684804038193343559153360000591890914138162679452520178353221126345668053628984789866309647708241703704572876397093327331829759682103901466789622570329436397304004981624979326705982863341122172795333419091029054076901225961700895404005870959370534342030325042659771283312708045031896875418423823654636664200180485341848613950104499288108479732463452304383581012867506699521685887270123864182790207674665585641962611326611636762153910224157810233669579162854801
```

This basically RSA encryption kinda thing but `e` value is very small because usually RSA encryption relies on high prime numbers so that it would be nearly impossible to factor.


# What RSA _expects_

RSA encryption is basically:

c=me(modn)c = m^e \pmod nc=me(modn)

Where

- **m** = message
    
- **e** = exponent
    
- **n** = giant number (product of two primes)
    

The **mod n** part is the security wall. It wraps the number around so you can't reverse it easily.

Think of it like a clock:

15 mod 12 = 3

Once numbers wrap around, the original value becomes hard to recover.

# The Mistake in The Challenge

Your exponent is:

e = 20

If the plaintext **m is small**, then:

m^20 < n

So the modulus never triggers.

Meaning encryption secretly becomes:

c = m^20

And reversing it is trivial:

m = 20th_root(c)

No factoring. No hacking. Just math.

That’s the **simple version of the attack**.


# Where Coppersmith Comes In

Coppersmith handles situations where the message is **almost small but not perfectly small**.

Imagine this instead:

c = m^20 mod n

But:

m^20 slightly bigger than n

Now the modulus wraps the number a little bit.

So the ciphertext becomes something like:

c = m^20 - k*n

for some unknown number **k**.

Now the equation becomes:

m^20 - k*n - c = 0

That looks ugly.

This is where **Coppersmith’s algorithm** steps in.


# The Core Idea (super simplified)

Coppersmith says:

> If a solution to a polynomial equation is **small enough**, we can still find it even when it's hidden inside a modulus.

So instead of brute forcing numbers, it uses **lattice math** (a type of linear algebra) to discover small solutions.

It’s like solving a puzzle where you know:

x^20 ≡ c (mod n)

and **x is small**.

Coppersmith reorganizes the math until the small root pops out.


# Python script to solve this Issue

```
# gmpy2 is a fast big‑integer math library.
# We use it because RSA numbers are enormous and normal math can be slow.

import gmpy2

# Utility from PyCryptodome that converts a large integer
# back into raw bytes (how RSA messages are actually stored).
from Crypto.Util.number import long_to_bytes


# The ciphertext from the challenge.
# In RSA this is the encrypted message represented as a huge integer.

c = 640637430810406857500566702096274083827969484683203431057884917289334852774>


# RSA public exponent.
# In this challenge it's small (20), which is the vulnerability.

e = 20


# iroot() computes the integer e-th root of c.
# It returns TWO things:
# 1) the root value
# 2) a boolean telling us if the root was exact.
#
# If the root is exact, it means:
#        c = m^e
# and the modulus (mod n) never wrapped the number.
# That means we can recover the plaintext directly.
m, exact = gmpy2.iroot(c, e)


# Prints whether the root was perfect.
# If True → the attack worked.
print("Exact root:", exact)


# Only convert the result if the root was exact.
# Otherwise the number isn't the real plaintext.
if exact:

    # RSA plaintexts are stored as numbers,
    # but the real message is bytes (ASCII text).
    # This converts the big integer back into readable bytes.
    print(long_to_bytes(m))
```

This script pretty much self explanatory and once you run this script it will give the flag. 

![](../../assets/Pasted%20image%2020260309160552.png)
The flag is not complete tho.