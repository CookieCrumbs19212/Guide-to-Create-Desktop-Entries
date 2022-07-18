# Guide to Create a Linux Desktop Entry

## How to create a desktop entry?
Desktop entries are created using `.desktop` files. These files allow your application (or any executable) to show up in the Application Launcher.  

___

### Step 1: Choose where to save the .desktop file

#### Is this desktop entry for all users or just you?
Decide whether you want to create the desktop entry for all users in your system or just for yourself. If you choose to create the desktop entry for all users, it will show up in the application launcher of every user in the system. Depending on the situation, you may or may not want everyone in the system to have the desktop entry pop up in their application launcher.

**NOTE**: You require root access to create the desktop entry for all users.  

**TIP**: When creating a desktop entry for all users, ensure that the executable file and app icon file are located in a directory accessable by root and outside any local user's file structure.  

#### Option 1: Create a desktop entry for all users:  
First you'll need to enable root privileges.  

```shell
$ sudo su
```  

Then enter the root password. This should give you root privileges.  

Next, `cd` to the `/usr/share/applications/` directory.  

```shell
$ cd /usr/share/applications/
```  


#### Option 2: Create a desktop entry just for yourself:
`cd` to the `~/.local/share/applications/` directory.  

```shell
$ cd ~/.local/share/applications/
```

___

### Step 2: Create the .desktop file
Let's say our application's name is *foo*. Then we will create the desktop file `foo.desktop` to store the desktop entry.

```shell
$ touch foo.desktop
```

___

### Step 3: Edit the .desktop file
Open the `.desktop` file you just created in your preferred code editor and paste the following code:  

```shell
[Desktop Entry]
Encoding=UTF-8
Version=1.0.0
Type=Application
Terminal=false
Exec=/path/to/executable/file
Name=Name of Application
Icon=/path/to/application/icon/file
```

Let's elaborate on the important variables:  
Variable | Description
---|---
`Version` | The version of the application, it is not a critical variable but you are free to modify it to reflect the version of the application.
`Terminal` | When set to `true`, a terminal will open up and run the executable. When set to `false`, the terminal is not opened up.
`Exec` | Absolute path to the executable file. All Linux executable files are accepted; shell, bin, etc.
`Name` | The name of your application. This is the name that will be displayed in the application launcher and show up in searches.  
`Icon` | Absolute path to the application icon file. The icon file can be almost any image file format. With that said, PNG format is desirable as it gives you the freedom of the alpha channel which allows for transparent backgrounds in the icon.  

Remember to save the changes made to the .desktop file.  

___

And that's it, you have successfully created a desktop entry for your executable.  
