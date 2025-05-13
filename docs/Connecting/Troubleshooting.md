
## VPN client doesn’t connect
- Check the username and password are correct - be careful not to add spaces, capitalisation etc
- Check the OTP code hasn't regenerated in the time taken to enter it
- If you’ve recently been sent a new ovpn file, make sure you have installed it.
- Check the OpenVPN log for ERROR messages

## OTP doesn't seem to work
- Sometimes the time synchronisation can be a little out.
	- Delete and reinstall the profile in your app.  
	- Try setting up the profile in a different app.

## Unable to connect to server
Indicated by error messages containing: “server not found” / “can not find specified endpoint”.

- Check that you’ve entered the server name correctly: _eldb.qmul-ceg.net_
- It can help some applications to specify that the connection uses TCP, either in a select dropdown or as a prefix: _tcp:eldb.qmul-ceg.net_
- If the server name still doesn’t work, try using the endpoint name:
	_tcp:ceg-mssql-02.czd1trqfl4br.eu-west-2.rds.amazonaws.com_)
- If that doesn’t work, try using the server’s IP address. This can change when the server is rebooted or updated, which is why it is recommend to use the server name or endpoint, if possible. The current server IP address is:
	_tcp:192.168.5.130_


