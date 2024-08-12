# CEG VPN Access Set Up

## Save Your OVPN Key File

You will receive a small ovpn file from CEG in the format _&lt;your name&gt;.ovpn._ This is a text file containing various keys, ie passwords, to allow you access to the CEG VPN. It is personal to you and **should be stored in a location on your device specific to your, such as your Documents or OneDrive. You can use it on multiple devices,** but you can only log into the VPN from one device at a time.

**Install an OpenVPN Client / Tunnelblick**

You will need to install a VPN client onto your laptop, PC or Mac that can handle OpenVPN protocols. We recommend:

- **OpenVPN GUI Community**: for Windows. Most users will need the 64-bit version. You can check your Windows version by right-click on Start, selecting System and looking under System Type.

Download the Windows MSI Installer from <https://openvpn.net/community-downloads/>

Note \- OpenVPN Connect is the VPN provided for commercial OpenVPN servers. It is free to download and will work with our OpenVPN server. However, it requires more memory to run and follows a separate update schedule.

- **Tunnelblick**: for Apple/Mac.

Download the latest stable release of <https://tunnelblick.net/downloads.html>

- Other VPN clients are, such as Pritunl and OpenConnect. CEG have done limited testing of these clients and so cannot provide any support on their setup, ovpn file import or use.

### Windows (OpenVPN)

Disconnect from any other VPN services you may be using, eg Cisco AnyConnect (EMIS web) before installing OpenVPN. If you are reinstalling OpenVPN, please uninstall the previous version first. It may help to also reboot your laptop or PC. You may need to restart Windows to complete the install.

Info available from: <https://community.openvpn.net/openvpn/wiki/OpenVPN-GUI>

Adding an ovpn file to a client requires Admin rights to the computer.

**Log into Windows with an Administrator level account. Once the OpenVPN client is installed, open it and click OK for** the popup that warns that there's no import file.

You will have a small OpenVPN tray icon on your taskbar. This may be hidden and you will need to make it visible. Right-click on the icon and select Import File.  
Browse to your ovpn file and click Open.  
OK the popup message.

If you are updating the ovpn file, also OK the warning that you are overwriting an existing file.

### MacOS (Tunnelblick)

Disconnect from any other VPN services you may be using before installing OpenVPN. If you are reinstalling OpenVPN, please uninstall the previous version first.

If you get a prompt asking if you wish to use the _openvpn-down-root_ plugin. Answer "yes" and Tunnelblick will use this plugin each time it makes a connection.

Info available from: <https://tunnelblick.net/czQuick.html>

Adding an ovpn file to a client requires Admin rights to the computer.

Once Tunnelblick is installed and running, simply drag and drop the ovpn file onto the Tunnelblick icon on your menu bar and select to install for Only Me.

You will need to provide an administrator password to allow the installation to run at root level.

## Install Duo Mobile

CEG will add you as a user in their CEG-AWS Duo account. Once this is ready, you will receive an email from Duo Mobile asking you to confirm and setup the account in your phone app.

You will need to install the _Duo Mobile_ app onto a smart device that will be available every time you wish to log into CEG-AWS. Android, Apple iOS apps are available via the appropriate app store.

Info will be provided in the email and is available from: <https://duo.com/product/trusted-users/two-factor-authentication/duo-mobile>

Click the link in the email and follow the instructions, providing user and phone details as required.

Scan the QR code when promoted.

Select to receive Duo messages by Push.

## Updating the OpenVPN Client and OVPN File

The OpenVPN client and Tunnelblick receive regular updates in order to patch vulnerabilities as well as add new features. It is important therefore to check every so often that you have the latest version installed. Reinstalling the OpenVPN client can often require a reboot.

On occasion you will be sent an updated ovpn file. This should have the same name as the previous ovpn file and can be imported into the client using the same method described above. You should get a popup message warning that you are overwriting an existing file – click to OK.