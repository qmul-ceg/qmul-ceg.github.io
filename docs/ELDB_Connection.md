East London Database

**Connecting to the ELDB Server**

# Overview

The East London Database is a series of annual databases containing data from the 1<sup>st</sup> April for patients registered with GP practices on that date. Full details of the included tables, the build business logic and commentary on how the data can be used are provided in a ‘Data and Schema’ document for the specific database. This guide provides information for connecting to the ELDB Server and to specific ELDB databases in order to conduct analyses.

## ELDB Server

The ELDB databases sit on the ELDB Server (Microsoft SQL Server), which is accessed by a username and password. This will be entered into the application you are using to connect to the server in order to query the data. See below.

## CEG VPN

The ELDB server is secured inside a Virtual Private Network (VPN) which can only be accessed via an OpenVPN server. User must have an OpenVPN client installed on their laptop or PC in order to establish the secure tunnel between their device and into the VPN. The VPN connection is authenticated by a confirmed notification from the Duo Mobile service. Users must also have, therefore, a Duo Mobile app installed on their smart phone. Together, these two authorisations create Multi Factor Authorisation (MFA).

In summary, users are authorised to access the VPN by 2 authorisations:

1. A personal .ovpn file containing the user’s personal key which authorises the device to connect to the OpenVPN server.
2. A confirmed Duo notification on the user’s smart phone.

## ELDB Sever Connection

Once a connection has been made into the VPN, the user connects to the ELDB Server using any application they choose that is capable of connecting to Microsoft SQL Server. They will need to provide their ELDB Server username and password where required, in order for the application to log into the server.

Some applications can query the SQL data directly, but many others need additional drivers or applications, such as ODBC drivers, to translate commands and queries. For many Microsoft applications, such as MS Access, it is necessary to install a special driver and setup a Data Source Name (DSN) within which to store the connection details.

## ELDB Query Software

The main applications that can be used to access the ELDB data are:

- **Microsoft Access**: Allows links to ELDB tables. Query using GUI. Requires:
  - ODBC driver
  - Setting up a User ODBC DSN
  - Running a VBA script, provided by CEG.
- **Azure Data Studio**: Enables a direct connection to the ELDB server and databases. Query using T-SQL.
- **SQL Server Management Studio**: Enables a direct connection to ELDB server and databases. Query using T-SQL.
- **SQL DBeaver**: Enables a direct connection to ELDB server and databases. Query using T-SQL. Requires:
  - JDBC driver – automatically installed
- **Power Query**: available as standard within Microsoft Excel and Power BI. Allows links to individual ELDB tables. Query using GUI and M (Power Query language). Requires:
  - ODBC driver
  - Setting up a User ODBC DSN
- **SQLCMD Utility**: The SQL Server Command Line Tool. This is bundled with the ODBC for SQL Server driver or can be downloaded separately. Enables a direct connection to an SQL Server using commands in the Command Prompt or PowerShell. This can be useful for managing a SQL Server password, as this facility is not readily available in MS Access, Power Query or DBeaver.

## 4 Step Setup

The process for connecting to ELDB should be understood therefore as 4 steps:

1. Setup applications for using the CEG VPN
    1. Install OpenVPN Client on laptop/PC
    2. Install Duo Mobile App on smart phone
2. Connect to CEG VPN
    1. Install ovpn key file
    2. Connect OpenVPN Client + Authorise Duo notification
3. Setup applications for querying the data
    1. Install preferred client, eg SSMS, MS Access, ADS
    2. If required install and setup additional drivers
4. Connect to an ELDB database
    1. Open application and enter username and password as required

This process can require a lot of software installation. As CEG does not manage or know about user’s particular hardware, network or other installed software, there is a limit to the amount of support CEG can provide for this process or for resolving problems. In many cases, installation issues will need to be handle by the device’s user or administrator. CEG can help with connection issues to the VPN and to the ELDB server.


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


# Connecting to the ELDB Server

Once you are connected to the CEG VPN, you can connect to the ELDB Server using your chosen application (MS Access, SSMS, Power BI etc).

You will need the ELDB Server endpoint, ie server name or IP address, and your username/password authentication for the ELDB server. This information is provided in the credentials sent to you by CEG.

Information for each application is available in the specific chapter. Some applications require an ODBC User DSN to be set up first.

## Connecting with Microsoft Access

GUI with linked tables

Requires **Setting Up an ODBC User DSN** + running a VBA script.

## Connecting with SQL Server Management Studio (SSMS)

Direct connection to ELDB server for querying using T-SQL.

## Connecting with Power Query (Excel / Power BI)

Connects to database tables as data sources which are transformed, using a GUI and M language (Power Query language), for uploading into Excel sheets or a Power BI model.

Requires **Setting Up an ODBC User DSN**

## Connecting with SQL DBeaver or other SQL Client

Direct connection to ELDB server for querying using T-SQL.

Requires a JDBC driver, which is automatically installed.

## SQLCMD Utility

Command Line Tool for creating a direct connection to the ELDB SQL Server. Bundled with the ODBC for SQL Server driver.

# Setting Up an ODBC User DSN

A Data Source Name (DSN) holds the connection information required for a data client on Windows to connect with a data source – in this case the ELDB Server. It specifies the ODBC driver to use and the server address. Both MS Access and Power Query (Excel and Power BI) use a DSN to connect to the ELDB server.

**Note:** The DSN specifies the connection to the server. The same DSN can be reused in different applications and instances of an application that links to differing databases on the server. (ie MS Access files setup for differing ELDB databases can use the same DSN, amended within the MS Access instance to link to a specified database).

## Install the ODBC Driver for SQL Server

The _ODBC Driver for SQL Server_ enables applications to connect and query data on a SQL Server. To check if it is installed on your PC:

Open the **ODBC Data Source Administrator (64-bit)** App by either

- _Control Panel > Administrative Tools > OBDC Data Source Administrator (64-bit)_
- _Programs > Windows Administrative Tools > OBDC Data Source Administrator (64-bit)_
- Search for _ODBC > OBDC Data Source Administrator (64-bit)_

Select the **Drivers** tab and look in the list for _ODBC Driver \[xx\] for SQL Server_

If it is not listed, download and install the ODBC driver from:

<https://learn.microsoft.com/en-us/sql/connect/odbc/download-odbc-driver-for-sql-server>

## Set up a User DSN

A \[Machine\] User DSN stores the connection information in the Windows Registry of the computer making it only available to the creating user and not able to be copied for one PC to another. For these reasons, it is best to set up a User DSN, rather than a System or File DSN.

In the ODBC Data Source Administrator (64-bit) app select the User DSN tab.

Click Add and in the Pop Up choose the ODBC Driver \[xx\] for SQL Server and click Finish.

![A screenshot of a computer


In the new Pop Up, add the following information:

Name: ELDB Server

Description: ELDB Server connection

Server: tcp:eldb.qmul-ceg.net

![A screenshot of a computer


Click **Next**

In the next screen, select **With SQL Server authentication using a login ID…** and enter your login ID and password.

![A screenshot of a computer


Click **Next**.

For the next few screens, ODBC Driver 18 for SQL Server has a slightly different setup to ODBC Driver 17 for SQL Server and earlier. Please follow the appropriate instructions.

### ODBC Driver 18 for SQL Server

Click **Next**.

Click **Next** again to move on 2 screens.

Tick Trust server certificate

![A screenshot of a computer


Click **Back** to navigate to the previous screen.

**Change the default database to** the most recent ELDB database or the one you usually connect to eg eldb2023. You will get a list of databases present on the ELDB server to choose from. Ignore any databases with suffixes (eg eldb2020_DEV) and any other non ‘eldb’ database names.

Note: this is the default database for the DSN. Other databases can be specified where it is used in an application.

Change the Application intent to READONLY.

![A screenshot of a computer


Click **Next** to return to the Trust server screen.

Click **Finish**.

### ODBC Driver 17 for SQL Server and earlier

Click **Next**.

**Change the default database to** the most recent ELDB database or the one you usually connect to eg eldb2023. Will get a list of databases present on the ELDB server to choose from. Ignore any databases with suffixes (eg eldb2020_DEV) and any other non ‘eldb’ database names. Change the **Application intent** to **READONLY**

![A screenshot of a computer


Click **Next**.

Tick Use strong encryption for data and Trust server certificate

![A screenshot of a computer


Click **Finish**.

## Check the Connection

For either Driver version, you should now reach a preview of the DSN configuration.

![A screenshot of a computer


Click Test Data Source.

If the connection fails, check back through the settings and re-enter your password – the password needs re-entering every time the DSN is edited or reviewed.

Once the Test works, Click **OK**.

The newly created DSN should be listed in the User DSN list.

Click **OK** to close the window.

# Connecting with Microsoft Access

Microsoft Access is a database application available within the Microsoft Office suite. It can link to tables within an East London Database using an ODBC driver within a user DSN. This should be setup to not download or copy the data to your device.

Whilst it is possible to host multiple connections within a single MS Access file, this could be cumbersome. We have found that queries joining tables from two databases run extremely slowly or never finishing at all. At the moment, therefore, cross database/year analysis is not possible. Our recommendation is to create separate MS Access database files for each database/year.

## ODBC Driver and User DSN

Before continuing with this setup, make sure you have completed the setup the ODBC driver and created a User DSN on your laptop or PC. Guidance is provided separately.

## Connect MS Access to the ELDB Server

Create a new Access database within a secure location.

In the new Access database, select to connect to a SQL Server or ODBC data source. Different versions of MS Access do this slightly differently. For instance:

Select External Data > From Database > SQL Server.

Select External Data > New Data Source > From Other Sources > ODBC Database.

Select Link the data source by creating a linked table and select OK.

In the Pop Up, select the Machine Data Source tab and then select the DSN that you created for the ELDB Server.

Click OK.

![A screenshot of a computer


In the SQL Server Login Pop Up, enter your password.

Click Options >> to display the additional settings

Set Database to the ELDB database that you wish to connect to eg eldb2022

An Option is also provided to change your password, if needed.

Click OK

![A screenshot of a computer


In the Link Tables dialog box, select each ELDB table with which you wish to link. ELDB tables and views are prefixed with dbo. Do not select any of the system tables (information_schema., sys.).

Each table has to be select one by one, using a mouse click or spacebar and arrow keys.

Click OK.

![A screenshot of a computer


A popup will warn that the table contains BigInt data type. Click Yes.

A second popup will warn that a data type is not backwards compatible. Click OK

This is required to stop the #Deleted error (see below).

The linked tables will appear in the Access left hand pane.

### Ticking Save Password

The Link Tables popup has a Save password option.

The recommendation is to NOT tick to Save the password.

Ticking this option means that you will not have to provide a password each time you use the database. However, the password is not encrypted and is saved within the file. A popup with this information will require clicking for every linked table ie if you select to link 80 tables, you will need to click a Save Password prompt 80 times.

### #Deleted Error

The ELDB database uses a datatype of ‘bigint’, which is not recognised as standard by Access and requires a change in the settings. Without this change, the ELDB data will be displayed as ‘#Deleted’.

![A screenshot of a computer


Changing the setting can either be done during the table linking, described above, or via the Access settings.

Select _File > Options > Current Database_

Scroll down to _Data Type Support Options_

Tick ‘Support Large Number (BigInt) Data Type for Linked/Imported Tables’ and OK

![A screenshot of a computer


A popup will warn you that must open and close the database. Click OK and reopen the database.

## Removing the dbo_ prefix

The linked tables appear in Access with a schema prefix (dbo_). This can be removed by running a Visual Basic script contained in the VB_remove_dbo.bas file provided by CEG. Download this file to your laptop or PC.

Within the Access database, open the Visual Basic module. This may be accessed in different ways depending on your version of MS Access. For instance:

Database Tools > Visual Basic

Select _File > Import File_ and select the VB_remove_dbo.bas file. Click Open.

Select _Run > Run Macro_ and Run the TruncateDBO macro.

Click OK to clear the message box.

Close the Visual Basic module.

It can take a couple of minutes for the table list to refresh, without the dbo_prefix.

## Adding Additional Linked Tables

Further tables can be later linked to the database.

In the Access database, open the Linked Table Manager:

Select External Data > Linked Table Manger

Tick the ODBC Data Source Name and click Add.

![A screenshot of a computer


Keep the Data source name as “ODBC” and select the data source as ‘Custom’.

![A screenshot of a computer


Click Next

In the Add New Link popup, fill in the Data Source Path with the ELDB hostname, prefixed with ‘tcp:’ – “tcp:eldb.qmul-ceg.net”.

![A screenshot of a computer program


Click Finish

As described above, select the DSN under the Machine Data Source

Provide your password.

And select the additional tables to link.

# Connecting with SQL Server Management Studio (SSMS)

SQL Server Management Studio (SSMS) is the SQL client provided by Microsoft. It can be downloaded for free from <https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver15>

All required drivers are installed with the application. A DSN is NOT required.

Open SSMS and select _Connect Object Explorer…_ from either the File menu or the ![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABEAAAAWCAIAAACpCuAVAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAAASdEVYdFNvZnR3YXJlAEdyZWVuc2hvdF5VCAUAAABwSURBVDhP1Y9RCoAgEAW7VnfyCl6xvvIEeY/EF4/HugoRJC3zseiM4LKn/JRZzXacFS73ro7TxBhDCAi4q+M0ax003NV53cDrQc02eLidUeNmOKfW/Y+OBoWJDaAN1LEN0MZcFX7ZEHNV8Jsx3zQpX4niUtgRQc6FAAAAAElFTkSuQmCC) icon at the top of the Object Explorer panel. A login window will appear. Enter the ELDB access credentials that you have been given.

![A screenshot of a computer


Click Connect

# Connecting with Azure Data Studio (ADS)

Azure Data Studio is an open-source SQL client developed by Microsoft but available for all platforms (Windows, Mac, Linux). It has a focus on data querying, rather than the wider data administration tasks available in SSMS. It is available for download from <https://learn.microsoft.com/en-us/sql/azure-data-studio/download-azure-data-studio?view=sql-server-ver16&tabs=redhat-install%2Credhat-uninstall>. It is also automatically installed with SQL Server Management Studio.

All required drivers are installed with the application. A DSN is NOT required.

Open SSMS and select the top icon, _Connections,_ from the lefthand sidebar. This will open the Connections panel. At the top of this panel, click on the left-hand icon (circled in red below) to create a _New Connection_.


The Connection panel will open on the right-hand side with the Connection Details section at the bottom.

![A screenshot of a computer


Change the _Authentication type_ to ‘SQL Login’ and enter the ELDB credentials that you have been given in the _Server_, _User name_ and _Password_ sections. Tick _Remember password._

_Database_ can be set to a specific database, such as ‘eldb2023’ – this will set the connection to that specific database. Alternatively, _Database_ can be left as ‘Default’ – this will set the connection to ELDB server, allowing you to see all the databases on the server. You will only be able to access, however, the databases to which you have been given the relevant permissions. See below for screenshots.

Change _Trust server certificate_ to ‘True’.

Provide a suitable name for the connection in the _Name(optional)_ section_._

If you’re password needs changing, the Change Password box will appear when you press _Connect_ or when you select the _Database_.

Choose a new password and _OK_.


If, at any point you get this connection error, click _Enable trust server certificate_. This will set the _Trust server certificate_ section in the Connection Details to ‘True’.


As explained above, connections made to the server will display all the databases on the server. Connections made to a specific database will show just that database. In each case, the database expands to a list of schemas and system folders. The database tables can be found under the _dbo_ schema.

You can set up multiple connections, of either type, and group them in the Connections panel. For instance, on the left below, each ELDB database has a separate connection under a ‘ELDB’ group. It is a matter of preference as to which connection method you choose.

| --- | --- |

There are many resources available online that provide an overview of ADS and its utilities. I recommend specifically looking at ADS’s Extensions module, for adding in extra features, and the Notebooks module, which enables executable SQL scripts to be embedded with text.

The Microsoft Learn pages are a good starting point, with some tutorials and how-to-guides.

<https://learn.microsoft.com/en-us/sql/azure-data-studio/what-is-azure-data-studio?view=sql-server-ver16>

# Connecting with Power Query (Excel / Power BI)

Power Query is a data preparation application integrated into many of Microsoft data products, most notably Excel 2016+ and Power BI. Similar to Microsoft Access, it is possible to link tables within an East London Database using an ODBC driver within a user DSN. This should be setup to not download or copy the data to your device.

## ODBC Driver and User DSN

Before continuing with this setup, make sure you have completed the setup the ODBC driver and created a User DSN on your laptop or PC. Guidance is provided separately.

## Switch Off Data Load

By default, Power Query will load the entire data connection, in this case an ELDB table, into the memory of its data model or into the Excel workbook. As some tables are millions of rows in size, this can take up a lot of memory and cause your application or device to slow down or even crash. It can also contravenes the CEG Data Policy that whole tables should not be downloaded to a local machine. It is important, therefore, to switch off this default setting.

### Excel

Go to _Get Data_ and select _Query Options_.

Under Global, select _Data Load_ and change the Default Query Load Settings to _Specify custom default load setting_.

Make sure _Load to worksheet_ and _Load to Data Model_ are unticked. Click OK.


### Power BI

Power BI does not have a global data load setting and some this must be managed for each linked table. When selecting a linked table from the Navigator (see below), do not choose to Load the data. Select _Transform Data_ to open the Power Query window, with the selected data links (queries). Right click on a query and untick _Enable Load_.


## Connecting with Excel / Power BI

Both Excel and Power BI use a similar GUI for external data connections.

Go to _Get Data_, select an ODBC connection.

In Excel, this is found _From Other Source_s >> _From ODBC_.

In Power BI it is _More… >> Other_ >> _ODBC_, and click Connect.

| Excel | Power Bi |
| --- | --- |

In the _From ODBC_ pop up, select the name of the DSN you created and OK.


Select _Link the data source by creating a linked table_ and select OK.

If required, provide your ELDB Server username and password.

In the Navigator window, select the table(s) you wish to link and click _Transform Data_ to open the Power Query window, with the selected data links, for further querying.

# Connecting with DBeaver or other SQL Clients

DBeaver is a SQL client that can connect to many different types of database. The free Community version is available from <https://dbeaver.io> and a portable version, that does not require an administrative login, can be downloaded from <https://portapps.io/app/dbeaver-portable/>. Other SQL clients can be used and will follow a similar connection process.

## Create a New Connection

In DBeaver, open a connection wizard by clicking on the plug icon in the upper left corner of the application window or go to Database >> New Database Connection. The database selection window will open with a long list of database connections. Select SQL Server and click Next.

Enter your ELDB access credentials, including your newly created password.

![A screenshot of a computer


Click Finish.

DBeaver will assess the connection requirements and may request that a JDBC driver is installed. Click OK and the driver will be automatically downloaded and installed.

# Connecting with SQLCMD

The SQL Server Command Line Tool (SQLCMD utility) is a SQL utility within the Command Prompt or PowerShell, installed with SSMS and the ODBC for SQL Server driver. It is useful for managing your password on the ELDB SQL Server, as this is less easily managed in the DSN or in DBeaver.

## Check for SQLCMD

To check if SQLCMD utility is installed on your PC, open a Command Prompt or PowerShell and type:

sqlcmd -?

If the SQLCMD utility is installed, the version number and list of available commands will displayed.

If SQLCMD is not installed, it can be downloaded from

<https://docs.microsoft.com/en-us/sql/tools/sqlcmd-utility?view=sql-server-ver15>

# Connecting with R and RStudio

To connect to the SQL server in R you will need the following libraries installed:

- _odbc_ – to make the connection to the ELDB server.
- _rstudioapi_ – to provide a secure password entry.
- _dplyr_ – to provide some query syntax.
- _dbplyr_ – to translate the _dplyr_ syntax to SQL.

Import the libraries and create a connection in your RStudio console:


A pop-up box will appear asking for your database password.


Once you enter your password, you are fully connected to the database and can now access all the available databases and tables under the Connections tab.


The _dbplyr_ and _dplyr_ libraries provide the syntax to pass the SQL data into R table objects.


Or the database can be queried directly using SQL.


# Troubleshooting

## OpenVPN works but I can’t connect to the ELDB Server

## “server not found” / “can not find specified endpoint” etc

- Check that you’ve entered the server name correctly:
  - _eldb.qmul-ceg.net_
- It can help some applications to specify that the connection uses TCP, either in a select dropdown or as a prefix:
  - _tcp:eldb.qmul-ceg.net_
- If the server name still doesn’t work, try using the endpoint name:
  - _tcp:ceg-mssql-02.czd1trqfl4br.eu-west-2.rds.amazonaws.com_)
- If that doesn’t work, try using the server’s IP address. This can change when the server is rebooted or updated, which is why it is recommend to use the server name or endpoint, if possible. The current server IP address is:
  - _tcp:192.168.5.130_

## OpenVPN login doesn’t work

- Check that you are putting the correct information into the OpenVPN login. It doesn’t’ use a username or password. In the credentials popup put:
  - Username = your ovpn file name. eg “danield”, if your file is danield.ovpn
  - Password = “PUSH”. This is command to push authentication to the Duo app.
- If you’ve recently been sent a new ovpn file, make sure you have installed it.
- Check the OpenVPN log
  - Right click on the tray icon and click View Log.
  - Errors will be flagged as ERROR and may help point you in the right direction
- Still not sure – save a copy of the log and attach in an email to CEG.

## Contacting CEG

Send queries to [m.a.sharp@qmul.ac.uk](mailto:m.a.sharp@qmul.ac.uk), who will assess and pass them on as required. We will respond within 48 hours.

| Date | Version | Information |
| --- | --- | --- |
| 19/06/2023 | 1   | Document Created |
| 01/09/2023 | 2   | Added information on Azure Data Studio<br><br>Added information on Power Query<br><br>Added Password section<br><br>Revised the Overview section<br><br>Removed the Table of Contents, as too difficult to maintain<br><br>Various formatting and typo corrections |
| 31/10/2023 | 3   | Added connecting to SQL server through R |
| 01/08/2024 | 4   | Updated and improved the Overview<br><br>Amended Setting Up an ODBC User DSN to emphasise that DSNs can be reused for different databases on the server.<br><br>Expanded the Troubleshooting section |