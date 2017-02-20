nppstub - Notepad++ Stub
=============

What is nppstub?
-----

It's a bash script that allows the integration of Notepad++/Wine with bash commands output files list and start Notepad++ as a native terminal command (root user included).

Install dependencies!
-----

 * The nppstub depends on Wine ("wine" and "winepath" commands) and the "realpath" command.

 - Install Wine...

```
apt-get install wine1.7 winetricks
```

 - Note I: To ensure compatibility with 32-bit applications on Wine...
 
```
apt-get install ia32-libs
```
 
 - Note II: To solve problems with fonts in Wine...

```
apt-get install ttf-mscorefonts-installer
```

Install as an integrated terminal command and enable it to root
-----

 - Install Notepad++ as your user and then as root (su)...

```
wine <filepath>/npp.6.7.9.2.Installer.exe
```

 - Create the folder below...

```
mkdir /home/[your_user]/.scripts
```

--------------
NOTE: For file ".bashrc" on Arch (or based) use...

```
vim /etc/bash.bashrc # For root configs!
vim /home/[your_user]/.bashrc # For your user configs!
```
--------------

 - Copy nppstub to scripts folder...

```
cp -avr [file_path]/nppstub /home/[your_user]/.scripts/
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

 - Example...
 
```
nppstub $(find ./ -name "*.py" -type f -exec grep -l 'some string' -- {} \;)
```

 - Note: In the above example we do a search ("find" command) for all files with extension "*.py" that have the content "some string" in your text!

PLUS!
-----

 - The following configuration is used to mount a samba share and avoids compatibility issues with Wine applications...

```
mount -t cifs -o noperm,username=<user name>,password=<password>,uid=1000,cache=none,auto,nounix <smb share> <folder to mount in>
```

Contact
-----

groovimdoc@gmail.com

Brazil-DF

<img border="0" alt="GrooVim Doc" src="http://upload.wikimedia.org/wikipedia/commons/thumb/6/6d/Map_of_Brazil_with_flag.svg/180px-Map_of_Brazil_with_flag.svg.png" height="15%" width="15%"/>
