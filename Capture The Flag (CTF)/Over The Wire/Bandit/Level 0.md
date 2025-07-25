This is the first challenge we are going to solve together. 

![[Pasted image 20250725082331.png]]

You ssh into the server using the command below 
![[Pasted image 20250725082618.png]]    When Prompted for the Password Enter  bandit0 
![[Pasted image 20250725083154.png]] If you enter the correct password, you’ll notice you’re logged in as user `bandit0`.

Once you’re in, run the `ls` command to see what files the user has. In this case, there’s a file called **readme**.

Next move? Read that file. You *could* use `nano` or `vim`... but let’s be real — that’s overkill for something this simple.

Just use:

```bash
cat readme
