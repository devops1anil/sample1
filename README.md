# Configure multiple github accounts on single machine(windows/linux)

## Windows
### Genarating ssh keys 
- For configuring multi github accounts on windows we can go with `SSH` and `HTTPS` .
 
 - In this case we are approched *ssh* based approch.
 
 - If you have been using windows10 first you need to start the `openssh`. click on search bar and type the services inside of that services you can findit.
 
 - Click on properties and select automatic and click on start button then it will move to start postion.

 - After starting the openssh go to terminal cmd or powershell or git bash.

 - In the powershell execute the command `ssh-keygen -t rsa -C "your github(personal)username/email"` .
 ```
 ssh-keygen -t rsa -C "your github(personal)username/email
 ```
 ```
 ssh-keygen -t rsa -C "your github(office)username/email
```
 
 - Save each key with unique names like `id_rsa_personal` or `personal` same with other account also.
 
### Add your ssh.pub key into github accounts

 - Login to github account and navigate to settings section inside of that find `ssh and gpg keys` click on that inside of that findout ssh keys.
 
 - In the ssh section click on `New SSH key` button. give the title for your new ssh key. select key type `Authentication key`, or ` sining key`.
 
 - Add .pubkey enscripted text in to key section and click on `add ssh key`.
 
 - same for both `personal` and `office` github accounts.
 
 - for copy the .pubkey text use this command in powershell `cat personal.pub_key(your .pub_key)`.
 
 - It shows the text inside of that file you can copy and paste it inside of key box.
 
### Add the SSH private keys to the agent:

 - when we adding these keys into agent it will store the data into cache we no need to enter passwords again and agin it will restore the credentioals.

 ```
ssh-add ~/.ssh/id_rsa_personal
```
```
ssh-add ~/.ssh/id_rsa_work
``` 
 - For adding keys you can execute above commands.
 
### Create or modify the SSH config file in .ssh folder :

 - In `/.ssh/` in this folder create a file and named it as a config file.

 - this is the sample config file 

```
# Personal account
Host github.com-personal
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa_personal

# Work account
Host github.com-work
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa_office
	
```
>**NOTE** this is the sample application for configuring multiple github accounts in a single machine.

click here for [refernce video](https://youtu.be/6lA0oPoFCAE?si=ICZMCZrDDn_XMJS_).
