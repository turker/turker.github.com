---
layout: post
title: Error installing the Azure SDK for Node.js and Windows azure web role entry point host crash
categories: Hope &nbsp This &nbsp Helps
---

Recently I have been developing  an application with a node.js and mongodb backend. I wanted to try deploying to Azure since it had Node.js support for a while now. 

I first installed the [Windows Azure SDK for Node.js](https://www.windowsazure.com/en-us/develop/nodejs/) and had couple of roadblocks on my way to the victory of running the app in the emulator. I wanted to list them here to help other brave souls who like to play with new-ish stuff.

## Error installing the Azure SDK for Node.js

The first issue that I had was the error in the installer. The installer was failing claiming that the dependency IISNode was not installed. I had IISNode already installed and it wasn't getting recognized. It took me several uninstalls and reinstalls of IISNode thinking that it had to be separately installed since there was no indication that it would be installed **with** the SDK. Finally when I tried uninstalling IISNode and letting the SDK installer run everything worked fine.

## Windows azure web role entry point host crash

The second blocker was the constant crashing of the web role entry point host. As there was no further exception detail in my environment I had to go fish out the IIS configuration hosts as I learned from [here](http://stackoverflow.com/questions/6692332/windows-azure-project-web-role-entry-point-host-stopped-error/8432621#8432621). The exception message was: 
>This access control list is not in canonical form and therefore cannot be modified.

[This](http://social.msdn.microsoft.com/Forums/da/windowsazuredevelopment/thread/07fe087e-4ac3-4c4f-bd62-4fccff4afd45) forum thread let me to this [blog post](http://blogs.msdn.com/b/avkashchauhan/archive/2011/10/18/windows-azure-application-launch-failed-with-an-error-quot-this-access-control-list-is-not-in-canonical-form-and-therefore-cannot-be-modified-quot.aspx) which solved the issue for me. The blog post had a couple implicit parts so below are the details:

* open regedit
* find the HKLM\Software\Microsoft\Windows Azure node
* open Permissions from the Edit menu of regedit
* Then you will get a dialog asking you to Re-Order the keys.
* Click on Re-Order and then Apply in the next dialog.


So there it is. I hope this helps if you are suffering from frustration while trying to play with Azure and node.js.