# Utilities
Common setup commands

## **Utility-1:** Make life easy, use Aliasing

- Save passwords/secrets in a .env file

```
export SECRET="YourPassword"
```

- do the following in ~/.bashrc or ~/.bash_profile.

```
source $filename.env
```

- The passwords/secrets are now exported in the respective environment variables
- Write a function for the alias command:

**SSH tunnel** (for jupyter, tensorboard)

```
sshTunnel()
{

	kill $(lsof -t -i:$PORT_NO)
	expect -c "spawn -ignore HUP ssh -N -L localhost:$PORT_NO:localhost:$PORT_NO username@ip; \
	expect \"password\";
	send $SECRET;
	exit 0"
	echo -e "\n"
	echo -e "http://localhost:$PORT_NO\n"
	open http://localhost:$PORT_NO
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
	echo -e "\n\n\n"
}
```

- \-ignore HUP runs the process in the background, eliminating the need to maintain a seperate terminal
- \-ignore HUP is not used in the second script since we want to keep the terminal in interactive mode.
- **Final Step:** 

```
alias ssh-serverA=sshServerA
alias jupyter-serverA=sshTunnel
```
ssh-serverA is now a command just like python, git etc.

### Voila! Life is easier now, isn't it ? 

## **Utility-2:** Remove long path structure in terminal

- Add the below line in bash rc to gid rid of the long path in terminal

```
PS1='\u:\W\$ '
```

## **Utility-2:** Connect to vpn via terminal (for Mac Users)

- Create a file secrets.env
- Add the following lines

```
export EMAIL="Youremail\r\n"
export PWD="Yourpwd\r\n"
```
- In ~/.bash_profile add the following:

```
source secrets.env

connectVpn()

{
expect -c "spawn /opt/cisco/anyconnect/bin/vpn connect vpn-address-here; \
expect \"Username\";
send $EMAIL;
expect \"Password\";
send $PWD;
interact"

}
alias connect-vpn=connectVpn

disconnectVpn()

{
/opt/cisco/anyconnect/bin/vpn disconnect;

}
alias disconnect-vpn=disconnectVpn
```
