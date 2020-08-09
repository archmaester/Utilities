# Utilities
Common setup commands

## Make life easy, use Aliasing

- Save passwords/secrets in a .env file
- do the following in ~/.bashrc or ~/.bash_profile.

```
source $filename.env
```

- The passwords/secrets are now exported in the respective environment variable
- Write a function for the alias command:

** SSH tunnel ** (for jupyter, tensorboard)

```
sshTunnel()
{

	expect -c "spawn -ignore HUP ssh -N -L localhost:$PORT_NO:localhost:$PORT_NO username@ip; \
	expect \"password\";
	send $SECRET;
	exit 0"
}
```

**SSH connection function**

```
sshServerA()
{

	expect -c "spawn ssh username@ip; \
	expect \"password\";
	send $SECRET;
	interact"
}
```

- \-ignore HUP runs the process in the background, eliminating the need to maintain a seperate terminal
- \-ignore HUP is not used in the second script since we want to keep the terminal in interactive mode.
- **Final Step:** 

```
alias ssh-serverA=sshServerA
alias jupyter-serverA=sshTunnel
```




