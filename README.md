nppstub - Notepad++ Stub
=============

<img border="0" alt="GrooVim Doc" src="http://imageshack.com/a/img829/4064/meg6.png" height="15%" width="15%"/>GrooVim Doc

What is nppstub?
-----

It's a bash script that allows the integration of Notepad++/Wine with bash commands output files list.

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
mkdir ~/scripts
```

 - Copy nppstub to scripts folder...

```
cp -avr <filepath>/nppstub ~/scripts/
```

 - Create a symbolic link to the root user (su)...

```
ln -s ~/scripts/ /root/scripts
```

 - Run...

```
export PATH=$PATH:/root/scripts # Logged in as root (su)!
export PATH=$PATH:~/scripts # Logged in as your user!
```

 - Add the line...

```
export PATH=$PATH:/root/scripts
```

... at the end of the file...

```
vi /root/.bashrc
```

 - Add the line...

```
export PATH=$PATH:~/scripts
```

... at the end of the file ...

```
vi ~/.bashrc
```

 - Run ...

```
source /root/.bashrc # Logged in as root (su)!
source ~/.bashrc # Logged in as your user!
```

... to reload the ".bashrc"!

 - Give permissions to your user...

```
chown -R eduardo /home/eduardo/scripts/*
chown -R :eduardo /home/eduardo/scripts/*
chmod -R 700 /home/eduardo/scripts/*
```

How to use!
-----

 - Model I (as an integrated terminal command)...

``` 
nppstub $(bash command)
```

 - Model II...

```
<file path>/nppstub $(bash command)
```

 - Example...
 
``` 
nppstub $(find ./ -name "*.py" -type f -exec grep -l 'some string' -- {} \;)
```

 - Note: In the above example we do a search (find command) for all files with extension "*.py" that have the content "some string" in your text!
