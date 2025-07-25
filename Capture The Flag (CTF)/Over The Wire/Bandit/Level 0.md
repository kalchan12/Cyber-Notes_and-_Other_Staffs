This is the first challenge we are going to solve together. 

<img src="../../../assets/Pasted%20image%2020250725145911.png" width="200%" />

You ssh into the server using the command below:

<img src="../../../assets/Pasted%20image%2020250725150030.png" width="200%" />

When prompted for the password, enter `bandit0`.

<img src="../../../assets/Pasted%20image%2020250725150055.png" width="200%" />

If you enter the correct password, you’ll notice you’re logged in as user `bandit0`.

Once you’re in, run the `ls` command to see what files the user has. In this case, there’s a file called **readme**.

Next move? Read that file. You *could* use `nano` or `vim`... but let’s be real — that’s overkill for something this simple.

Just use:

```bash
cat readme
