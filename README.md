# BasicPiSetUp
Files and Commands to get Raspberry Pi's up and running, common early set up changes, etc


# Replace 'pi' user with your own name



## Step 1

To change the pi user to junglegeorge, you must login as root user. You cannot change pi while you're logged as pi, of course. To be able to login as root you must enable root.
Login to pi: Login: pi, password: raspberry

```
sudo passwd root
```

## Step 2

Enable root login on SSH, edit the sshd_config file:

```
sudo nano /etc/ssh/sshd_config
```


Add the `PermitRootLogin yes` line so it will look like this:

```
# Authentication:

#LoginGraceTime 2m
#PermitRootLogin prohibit-password
PermitRootLogin yes
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10
```

Restart SSH server to take effect:

```
sudo service ssh restart
```

## Step 3

Now logout of the user pi using the command:

```
logout
```

Login again into the pi as user `root` with password created in step



## Step 4

Swap in new name for pi: 

```
usermod -l kevin pi
```


## Setp 5

Now that user name has been changed, the user's home directory should also be changed to reflect the new login name


```
usermod -m -d /home/kevin kevin
```

## Setp 6

Rename pi group to the one also named kevin. So you belong to your own group, as pi belong to pi group.


```
groupmod -n kevin pi
```


## Step 7 

Log out of root user and back in as yourself

```
logout
```

## Step 8

Change your password!

```
passwd
```

Type your new password, then retype/confirm it

```
XXX
```


```
XXX
```


```
XXX
```


```
XXX
```












# Change Hostname
Your Raspberry Pi's name is in a file called 'hostname' in the /etc directory.  Edit that file as superuser with:

`sudo nano /etc/hostname`

This file contains only one line - the hostname of your Raspberry Pi.  Change the name to whatever you like, but only use the letters 'a' to 'z' (upper or lower), digits '0' to '9', and the dash '-'.

There is a second file that also contains the hostname, but it is only there as a workaround for some software.  Therefore you should also edit that file:

`sudo nano /etc/hosts`

Find the line starting with 127.0.0.1, and change the name following it to your new hostname.  Save the file using Ctrl+x, then Y followed by Enter.

Once you have rebooted your Raspberry Pi, all other computers on your network should see it with the new hostname.  On the Raspberry Pi itself, you can check your hostname by issuing the following command in a terminal window:

`hostname`

