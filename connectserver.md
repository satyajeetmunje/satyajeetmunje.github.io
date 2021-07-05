layout: page
title: "Connect Server"
permalink: about/connectserver

# Overview

Desktop and Mobile client synchronization with OwnCloud server.

# Installing the Desktop Synchronization Client

Download the latest version of the ownCloud Desktop Synchronization Client from the [ownCloud download page](https://owncloud.org/install/#desktop). There are clients for Linux, Mac OS X, and Microsoft Windows.

## A) For Mac OS X and Windows Users

Installation on Mac OS X and Windows is the same as for any software application as:

1. Download the program.
2. Double-click downloaded program to launch the installation.
3. Follow the installation wizard. 

### Installation Wizard

The installation wizard takes you step-by-step through configuration options and account setup. 

1. Enter the web address of your ownCloud server https://studio/owncloud. Click **Next**.

##Enter image

2. Enter your ownCloud **Username** and **Password** login credentials. Click **Next**.

##Enter image

3. On the **Setup local folder options** page you can sync all of your files on the ownCloud server, or select individual folders. 
The default local sync folder is ownCloud, in your home directory. <br>
You can change this if needed.

##Enter image

4. When selection of sync folders completes, click **Connect**. The client establishes connection to your ownCloud server.
   Once connection is established successfully, it starts synchronizing your files and following two buttons are displayed:
   
  - Open ownCloud in Browser (To connect to your ownCloud Web GUI)
  - Open Local Folder (To open your local folder)
 
##Enter image

5. Click **Finish**.

## B) For Linux Users

For Linux users, follow the instructions on the download page to:

1. Add the appropriate repository for Linux distribution.
2. Install the signing key.
3. Use package managers to install the desktop sync client. 

Linux users update their sync clients via package manager, and the client displays a notification when an update is available.

***IMPORTANT***
>
>To login sync client automatically, password manager should be enabled. For example, [GNOME Keyring](https://wiki.gnome.org/Projects/GnomeKeyring/) or [KWallet](https://utils.kde.org/projects/kwalletmanager/).

# Synchronization Using the ownCloud Mobile App

## Installing

To get your ownCloud Android app, log into your ownCloud server from your Android device using a Web browser such as Chrome, Firefox, or Dolphin.

The first time you log into a new ownCloud account, a screen with a download link to the ownCloud Android App in the [Google Play Store](https://play.google.com/store/apps/details?id=com.owncloud.android) is available.

##Enter imag

Find source code and more information from the [ownCloud download page](http://owncloud.org/install/#mobile). 

## Connecting to Your ownCloud Server

When you run your ownCloud Android app for the first time, configuration screen opens. On the configuration screen, follow below steps:

1. Enter your server web address.
2. Login name and password.
3. Click **Connect**. 

*Tip*
>
>To see your password, click the **eyeball** to the right side of your password.

##Enter imag

For best security, your ownCloud server should be [SSL-enabled](http://info.ssl.com/article.aspx?id=10241) so that you can connect via HTTPS.<br>
If your server has a self-signed SSL certificate, a warning message is displayed, ”Do you want to trust this certificate anyway?”<br>
If this happens, click **Yes** to accept the certificate and complete your account setup.

##Enter imag

ownCloud Android App connection is established with server OwnCloud server.





