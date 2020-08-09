# Utilities
Common setup commands for Mac users

## **Utility-1:** Make life easy, use Aliasing

- Create a file secrets.env
- Save passwords/secrets in the file

```
export SECRET="YourPassword\r"
```

- do the following in ~/.bashrc or ~/.bash_profile.

```
source secrets.env
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
- Create alias 

```
alias ssh-serverA=sshServerA
alias jupyter-serverA=sshTunnel
```
- Run the required command in terminal

```
> ssh-serverA
```
or
```
> jupyter-serverA
```

## **Utility-2:** Remove long path structure in terminal

- Add the below line in bash rc to gid rid of the long path in terminal

```
PS1='\u:\W\$ '
```

## **Utility-3:** Connect to vpn(using Cisco Anyconnect) via terminal (for Mac Users)

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
- In your terminal

For the changes to be effective (one-time)
```
> source ~/.bash_profile
```
**Before running the below command, quit/force-quit the UI-application**

To connect to vpn
```
> connect-vpn
```

To disconnect

```
> disconnect-vpn
```
