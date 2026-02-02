The objective of this page is to give details about running Steam and a Windows application (in my case, Rockstart Games Launcher) on top of Linux Fedora (it could also be another distribution but staeps may be slighlty differents) without needing Windows Operating System.

This is an aggregate of information of what I know and what I have found to get those little issues fixed.

# 1/ Install Fedora
I won't details this part as it is straight forward and well explained in Fedora documentation.

I have installed **Fedora KDE Plasma 43**.

# 2/ Install Steam
Source: [https://docs.fedoraproject.org/en-US/gaming/proton/]

I chose the terminal steps (Go to **Application Launcher > Konsole**):
```
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm -y
sudo dnf config-manager setopt fedora-cisco-openh264.enabled=1
sudo dnf install steam -y
```

If Steam is starting but not opening, it is most likely it is the same error as mine (steamwebhelper is crashing - you can see details running journal -f from Konsole and reopen Steam).

In this case, just start Steam from Konsole terminal:
```
steam
```
This time it should open. 

From there, go to **Setting > Interface and disable "Enable GPU accelerated rendering in web views (requires restart)"**.

After that, your steam client interface should work and you can install your games the same way as it is on Windows.

# 3/ Third Party application
Some of the games are not from Steam, but no worries, you can still ink them back to Steam.

For example, I have Red Dead Redemption 2 which is coming from Rockstart Games Launcher only providing a Windows .exe file.

In this case, you need to use Wine which will provide a compatibility layer between your windows Application and your Linux Operating System.

First step it to install Wine and Wineglass (providing a GUI) from the Software Centre.

After that, open Wineglass:
```
-Create a new prefix (Name is not important)
-When it is created, click on the arrow to Run .exe file
-Search for your .exec file (mine is Rockstar-Games-Launcher.exe)
-This will trigger the client installation
```

Final step, from Steam client, go to **Library > Add a Game** and look for the Rockstar Games Launcher.
From there, you can play to this new game.
