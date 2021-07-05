layout: page
title: "Connect Server"
permalink: about/connectserver

# Overview

Desktop and Mobile client synchronization with OwnCloud server.

# Installing the Desktop Synchronization Client

Download the latest version of the ownCloud Desktop Synchronization Client from the [ownCloud download page](https://owncloud.org/install/#desktop). There are clients for Linux, Mac OS X and Microsoft Windows.

## System Requirements

- Windows 7+ (x86 with 32-bit or x86-64; Native WinVFS available for Windows 10 version 1709 or later)

- macOS 10.12+ (x86-64 or Apple M in Rosetta 2 emulation; unsupported legacy builds for Mac OS X 10.10 & 10.11 available)

- CentOS 7.6+ & 8 (x86-64)

- Debian 9.0 & 10 (x86-64)

- Fedora 31 & 32 & 33 (x86-64)

- Ubuntu 18.04 & 20.04 & 20.10 & 21.04 (x86-64)

- openSUSE Leap 15.1 & 15.2 (x86-64)

*Note*
>
>For Linux distributions, the latest two versions per platform and the previous Ubuntu [LTS](https://wiki.ubuntu.com/LTS).

## A) For Mac OS X and Windows Users

Installation on Mac OS X and Windows is the same as for any software application as:

1. Download the program.
2. Double-click program to launch the installation.
3. Follow the installation wizard. 

### Installation Wizard

The installation wizard takes you step-by-step through configuration options and account setup. 

1. Enter the web address of your ownCloud server https://studio/owncloud. Click **Next**.

![Enter server address](https://github.com/satyajeetmunje/satyajeetmunje.github.io/blob/main/Page2.1.png)

2. Enter your ownCloud **Username** and **Password** login credentials. Click **Next**.

![Login Credentials](https://github.com/satyajeetmunje/satyajeetmunje.github.io/blob/main/Page2.2.png)

3. On the **Setup local folder options** page you can sync all of your files on the ownCloud server, or select individual folders. 
The default local sync folder is ownCloud, in your home directory.
You can change this if needed.

![Sync Files](https://github.com/satyajeetmunje/satyajeetmunje.github.io/blob/main/Page2.3.png)

4. When selection of sync folders completes, click **Connect**. The client establishes connection to your ownCloud server.
   Once connection is established successfully, it starts synchronizing your files and following two buttons are displayed:
   
  - Open ownCloud in Browser (To connect to your ownCloud Web GUI)
  - Open Local Folder (To open your local folder)
 
![Setup Finish](https://github.com/satyajeetmunje/satyajeetmunje.github.io/blob/main/Page2.4.png)

5. Click **Finish**.

After it is installed and configured the sync client automatically keep itself updated. See [The Automatic Updater](https://doc.owncloud.org/desktop/2.0/autoupdate.html) for more information.

## B) For Linux Users

For Linux users, follow the instructions on the download page to:

1. Add the appropriate repository for Linux distribution.
2. Install the signing key.
3. Use package managers to install the desktop sync client. 

Linux users update their sync clients via package manager, and the client displays a notification when an update is available.

*Note*
>
>To login sync client automatically, password manager should be enabled. For example, [GNOME Keyring](https://wiki.gnome.org/Projects/GnomeKeyring/) or [KWallet](https://utils.kde.org/projects/kwalletmanager/).

# Synchronization Using the ownCloud Mobile App

## Installing

To get your ownCloud Android app, log into your ownCloud server from your Android device using a Web browser such as Chrome, Firefox, or Dolphin.

The first time you log into a new ownCloud account, a screen with a download link to the ownCloud Android App in the [Google Play Store](https://play.google.com/store/apps/details?id=com.owncloud.android) is available.

![App Download](https://github.com/satyajeetmunje/satyajeetmunje.github.io/blob/main/Screen3.1.png)

Find source code and more information from the [ownCloud download page](http://owncloud.org/install/#mobile). 

## Connecting to Your ownCloud Server

When you run your ownCloud Android app for the first time, configuration screen opens. On the configuration screen, follow below steps:

1. Enter your server web address https://studio/owncloud.
2. Enter you login name and password.
3. Click **Connect**. 

*Tip*
>
>To see your password, click the **eyeball** to the right side of your password.

![Configuration Screen](https://github.com/satyajeetmunje/satyajeetmunje.github.io/blob/main/Screen3.2.png)

For best security, your ownCloud server should be [SSL-enabled](http://info.ssl.com/article.aspx?id=10241) so that you can connect via HTTPS.
If your server has a [self-signed SSL certificate](https://www.digitalocean.com/community/tutorials/how-to-create-a-self-signed-ssl-certificate-for-apache-in-ubuntu-16-04), a warning message is displayed, ”**Do you want to trust this certificate anyway?**”.<br>
If this happens, click **Yes** to accept the certificate and complete your account setup.

![Trust Certificate](https://github.com/satyajeetmunje/satyajeetmunje.github.io/blob/main/Screen3.3.png)

ownCloud Android App connection is established with OwnCloud server.





