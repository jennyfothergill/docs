# Mapping a Network Drive

Procedures for mounting the directory are different depending on which OS you
are using.
Some things to keep in mind:

- VPN is required if trying from off campus
- If you are using a personal computer, you need to provide your username in a specific format using a backslash: `boisestate\username`
- Windows path: `\\cifs-prd-01\Research\pi_username`
- Mac path: `smb://cifs-prd-01/Research/pi_username`

**Replace `username` with your Boise State username and `pi_username` with the username of the PI who owns the research share!**

## Connect from a non-domain attached computer
### On Campus
You should use a hard-wired connection if possible. The Bronco-Guest wifi network cannot access the systems which are behind a firewall. However, you can use the wireless network named "eduroam" as it is an authenticated connection.  

### Off-campus
You will need to connect with the GlobalProtect VPN client before trying to connect to the department drives.

## Windows
Use the "Map Network Drive" utility available in Windows Explorer or My Computer.
Select which drive letter you want to map. Note any available drive letter can be assigned as the drive letters are just pointers.
Type in the folder path for which mapping you want.

Folder path\*:
`\\cifs-prd-01\Research\pi_username`

By default the "Reconnect at logon" option is selected. Unselect this.
Select the "Connect using different credentials" option.

When prompted for your credentials, enter it in `domain\username` format (i.e., `boisestate\username`)\*.
Type in your boisestate password and authenticate.

\*Make sure you use backslashes, not forward slashes.
## Mac
From the main Finder menu, select "Go", then "Connect to Server".
Connect using an SMB connection.

Folder path:
`smb://cifs-prd-01/research/pi_username`

If your Mac is integrated into Active Directory, you will not be prompted for your username/password. If your Mac is not integrated into AD, you will be prompted for your boisestate username/password when you connect.
When prompted for your credentials, enter it in `domain\username` format (i.e., `boisestate\username`)\*.
Type in your boisestate password and authenticate.

\*Make sure you use backslashes, not forward slashes.
