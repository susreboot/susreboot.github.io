---
title: "Install Windows 11 Without a Microsoft Account (Local Account)"
date: "2023-02-20"
categories: 
  - "tips"
  - "windows"
---

There are a few different ways to create a local account while installing Windows 11 and I will explain a few (for large enterprise environments you should be using [Windows Autopilot](https://learn.microsoft.com/en-us/mem/autopilot/windows-autopilot)). The reason you would want to do this is you don't want to connect your computer to a Microsoft Account. I personally don't like having a Microsoft account connected to my computer to use it.

You will follow Windows 11 install process until you will come to the screen that asks you to add your Microsoft account.

From here there are three different ways to add a local account:

## Out-of-box experience Bypass

At the "Add your Microsoft Account" Page you will;

1. Press **Shift+F10**

3. A Command Prompt will appear

5. Enter this command: **OOBE\\BYPASSNRO**

7. The computer will restart and the OOBE (out-of-box experience) will start again

9. Click the "I don't have internet" option on the "Let's connect you to a network"

11. Click the "Continue with limited setup" option.

13. A screen should appear that says "Who's going to use this device?"

15. Enter your **Local Username**

17. Select "Next"

19. Enter your **Local Password**

21. Select "Next"

## Releasing IP Address

At the "Add your Microsoft Account" Page you will;

1. Press **Shift+F10**

3. A Command Prompt will appear

5. Enter this command: **ipconfig /release**

7. Close the Command Prompt window

9. **Click the back arrow** (located at the top left of the screen)

11. A screen should appear that says "Who's going to use this device?"

13. Enter your **Local Username**

15. Select "Next"

17. Enter your **Local Password**

19. Select "Next"

## Using Fake Email

At the "Add your Microsoft Account" Page you will;

1. enter **no@notarealdomain.com**

3. Select "Next"

5. Enter a random password

7. Select "Sign in"

9. If this method works you should get to a screen that say "Oops, something went wrong"

11. Select "Next"

13. A screen should appear that says "Who's going to use this device?"

15. Enter your **Local Username**

17. Select "Next"

19. Enter your **Local Password**

21. Select "Next"

Sources:

[https://pureinfotech.com/bypass-internet-connection-install-windows-11/#:~:text=a%20second%20layout.-,On%20the%20%E2%80%9COops%2C%20you've%20lost%20internet%20connection%E2%80%9D,Windows%2011%20and%20press%20Enter.](https://pureinfotech.com/bypass-internet-connection-install-windows-11/#:~:text=a%20second%20layout.-,On%20the%20%E2%80%9COops%2C%20you've%20lost%20internet%20connection%E2%80%9D,Windows%2011%20and%20press%20Enter.)

[https://www.windowscentral.com/how-set-windows-11-without-microsoft-account](https://www.windowscentral.com/how-set-windows-11-without-microsoft-account)

[https://www.tomshardware.com/how-to/install-windows-11-without-microsoft-account](https://www.tomshardware.com/how-to/install-windows-11-without-microsoft-account)
