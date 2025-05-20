# Required Software
## VPN Client
You will need to install a VPN client onto your laptop, PC or Mac that can handle OpenVPN
protocols. We recommend:

- [OpenVPN GUI Community 64-bit](https://openvpn.net/community): a lightweight  open-source app for **Windows
- [OpenVPN Connect](https://openvpn.net/client/): a slicker but more resource heavy freeware app for **Windows / Mac / Linux**
- [Tunnelblick](https://tunnelblick.net/downloads.html): the standard VPN client for **Mac**

Adding an ovpn file to a client by default requires Admin rights to the computer. Change the Profiles folder to within the user area. 

Disconnect from any other VPN services you may be using, eg Cisco AnyConnect (EMIS web) before installing the VPN client. If you are reinstalling, it is best to uninstall the previous version first. It may help to also reboot your laptop or PC after the install.

The OpenVPN GUI app does not have an automated update facility.  If it is installed on an unmanaged laptop or PC, users should regularly check for updates and re-install if needed.  Tunnelblick and OpenVPN Connect should automatically keep themselves up to date. 
   
### Further Information  

- [OpenVPN Community Wiki: Using OpenVPN GUI](https://community.openvpn.net/openvpn/wiki/OpenVPN-GUI-New)
- [OpenVPN Documentation: Connect Client](https://openvpn.net/client/client-connect-vpn-for-windows/)
- [Tunnelblick Quick Start Guide](https://tunnelblick.net/czQuick.html)

## OTP Authenticator
CEG-VPN3 uses TOTP for multi-factor authentication.  You can use any TOTP authenticator phone app compatible with Google Authenticator, which includes the Duo Mobile that you would have used to connect to CEG-VPN2 or CEG-VPN1.  Other suitable apps are Google Authenticator, Microsoft Authenticator, Authy, 2FAS Auth and many others.  All are available in the appropriate app store.

Where it is provided, app unlock security such as PIN or biometrics, should be used.  Screenshots inside the app should be switched off.  Care should be taken about the storage location for any backup facility. 

