nppstub - Notepad++ Stub
=============

What is nppstub?
-----

It's a bash script that allows the integration of Notepad++/Wine with bash commands output files list and start Notepad++ as a native terminal command (root user included).

Install dependencies!
-----

The nppstub - of course - depends on Wine ("wine", "winepath" and "realpath" commands basically).

Install as an integrated terminal command and enable it to root
-----

 - Install Notepad++ as your user and then as root (su) and create the folder below...

```
mkdir /home/[your_user]/.scripts
```

-----
NOTE: For the file ".bashrc" on Arch (or based) use...

```
vim /etc/bash.bashrc # For root configs!
vim /home/[your_user]/.bashrc # For your user configs!
```
-----

 - Copy nppstub to scripts folder...

```
cp -avr [file_path]/nppstub/nppstub /home/[your_user]/.scripts/
```

 - Create a symbolic link to the root user (su)...

```
ln -s /home/[your_user]/.scripts/ /root/.scripts
```

 - Run...

```
export PATH=$PATH:/root/.scripts # Logged in as root (su)!
export PATH=$PATH:/home/[your_user]/.scripts # Logged in as your user!
```

 - Add the line...

```
export PATH=$PATH:/root/.scripts
```

... at the end of the file...

```
vi /root/.bashrc
```

 - Add the line...

```
export PATH=$PATH:/home/[your_user]/.scripts
```

... at the end of the file ...

```
vi /home/[your_user]/.bashrc
```

 - Run ...

```
source /root/.bashrc # Logged in as root (su)!
source /home/[your_user]/.bashrc # Logged in as your user!
```

... to reload the ".bashrc"!

 - Give permissions to your user...

```
chown -R <your user> /home/[your_user]/.scripts/*
chown -R :<your user> /home/[your_user]/.scripts/*
chmod -R 700 /home/[your_user]/.scripts/*
```

 - At the end of the nppstub file where the lines...
 
```
eval "/usr/share/playonlinux/playonlinux --run \"notepad++\" -multiInst -nosession $INPUT_FILES 2> /dev/null 1> /dev/null &"
```

... and...

```
eval "env WINEPREFIX=\"$HOME/.wine\" wine \"C:/Program Files (x86)/Notepad++/Notepad++.exe\" -multiInst -nosession $INPUT_FILES 2> /dev/null 1> /dev/null &"
```

... make the adjustments according to the installation of Notepad++ in your Wine.

How to use!
-----

 - Model I (as an integrated terminal command)...

``` 
nppstub $(bash command)
```

 - Note: If you run the "nppstub" command without passing any parameters Notepad++ will simple starts!

 - Model II...

```
<file path>/nppstub $(bash command)
```

 - One example...
 
```
nppstub $(find ./ -name "*.py" -type f -exec grep -iFl 'some string' -- {} \;)
```

 - Note: In the above example we do a search ("find" command) for all files with extension "*.py" that have the content "some string" in your text!

TIP!
-----

 - The following configuration example is used to mount a samba share and avoids compatibility issues with Wine applications (like Notepad++)...

```
mount -t cifs -o noperm,username=<user name>,password=<password>,uid=1000,cache=none,auto,nounix <smb share> <folder to mount in>
```

Contact
-----

groovimdoc@gmail.com

Brazil-DF

<img border="0" alt="GrooVim Doc" src="http://upload.wikimedia.org/wikipedia/commons/thumb/6/6d/Map_of_Brazil_with_flag.svg/180px-Map_of_Brazil_with_flag.svg.png" height="15%" width="15%"/>
