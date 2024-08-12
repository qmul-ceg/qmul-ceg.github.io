# Connecting to the CEG VPN

## Connect to CEG-VPN

Right-click the OpenVPN tray icon on your taskbar or click the Tunnelblick icon on your status bar and click Connect. A window will appear with connection messages.

On the first-time logging in, you will need to provide username/password information.

Username: your ovpn file name. eg “danield”

Password: “push”

These are instructions for the OpenVPN/Duo system and not an actual username/password.

Click or Tick to Save the Password.

Click OK or wait 5 seconds for the client to automatically make the connection.

The connection window will show various messages, including that it is sending PUSH REQUEST messages.

You should receive a Duo notification on your phone. Sometimes this is a bit slow, and you may need to open the app to see the notification. Tap Accept on the notification.

The connection window will take a few more seconds to complete the connection messages and then close or can be closed.

Once connected, the OpenVPN tray icon will show as green or the Tunnelblick icon will be highlighted.

More information can be found:

<https://community.openvpn.net/openvpn/wiki/OpenVPN-GUI>

<https://tunnelblick.net/czQuick.html>

Disconnect from CEG-VPN

When you have finished using ELDB, disconnect from the server in the software that you are using and then disconnect from the VPN. Disconnecting from the VPN whilst still connected to a resource can cause some programmes to hang for a short while.

Right-click the OpenVPN tray icon on your taskbar and click Disconnect.

Or click on Disconnect in the Tunnelblick menu icon and Quit.

# Your ELDB Server Username and Password

CEG will provide you with a csv file containing the access and authentication details for the ELDB server. This will be sent separately to the CEG-VPN credentials. The credentials consist of:

- **server address** – this is an internet address setup to link to the ELDB server. It is the primary address to use when setting up a connection.
- **server name** – this is the name of the server used by the hosting service (Amazon Web Services). If there is a problem with the server address, the server name may work instead.
- **server IP** – this is the actual address of the server on the network. If the server address and server name don’t work, the server IP should work. However, the server IP is not static and can change if the server is rebooted during maintenance. It is advisable where possible therefore to use either the server address or name.
- **username** – this is your login specifically for the ELDB server.
- **password** – this is a lengthy set of random characters specific to your username, created by CEG. It does not require changing but you can change it, as described below.

Your password must be stored in a secure location. The recommendation is to use a Password Manager such as BitWarden (<https://bitwarden.com/>) or KeepassXC (<https://keepassxc.org/>).

Changing Your Password

CEG will provide you with a strong password for the ELDB Server. Previously, the requirement was for this to changed on first login. This caused problems for some users attempting to connect with applications that didn’t have password management facilities. The policy has changed, therefore, to using complex static passwords. However, users are able to change this password to one more suitable for their specific needs, or if they believe the password may have been compromised.

The user generated password must:

- be unique to the ELDB Server login.
- be at least 12 characters.
- be at least 4 words long, if created using a passphrase or diceware system.
- have a calculated entropy of 60+

Password generators are available online, including:

<https://rumkin.com/tools/password/>

<https://diceware.dmuth.org/>

### Changing your Password using SQL

This is the simplest method, if you have an SQL client (SSMS, ADS, DBeaver etc) that is connected to the ELDB Server. Even if you don’t use SQL for data querying, it may be useful to have a SQL client connection specifically for this purpose.

In the SQL client, create a new query and enter:

ALTER LOGIN _&lt;username&gt;_

WITH PASSWORD = '_&lt;new password&gt;_'

OLD_PASSWORD = '_&lt;old password&gt;_'

Note the single quotes around the new and old passwords.

Run the query and check that no error messages are returned.

You will need to separately change any connection details in your applications to the new password.

### Changing your Password using MS Access

This method requires that you have an ODBC DSN set up for the ELDB Server for use in Microsoft Access.

Create a new Access database and proceed in the same way as instructed below for linking ELDB tables to Access:

Select to connect to a SQL Server or an ODBC data source.

Select _Link the data source by creating a linked table_ and select the DSN that you created for the ELDB Server under the Machine Data Source tab.

In the SQL Server Login Pop Up, enter your old (or current) password and click _Options >>_ to display the additional settings.

Confirm that Database refers the right database.

Tick _Change Password_ and provide a new password


Click OK and then OK to close the _Link Tables_ window. OK and Close any still open windows and then the Access database.

Your password will have now been changed on the server and so can be used or changed in any other Access databases or applications you use.

### Change your SQL Server Password in SQLCMD

This is another simple method, if you have SQLCMD installed on your device.

Open a Command Prompt or PowerShell and type:

sqlcmd -S eldb.qmul-ceg.net -U &lt;username&gt; -P &lt;password&gt; -Z &lt;new password&gt;

Press enter to run the command. If there are no problems, the cursor will open a new line as 1>. Type exit to leave the utility.
