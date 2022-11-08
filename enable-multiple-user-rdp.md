# enable multiple user rdp


## Enable Multiple RDP Sessions

```
- Log into the server, where the Remote Desktop Services are installed.
- Open the start screen (press the Windows key) and type gpedit.msc and open it.
- Go to Computer Configuration > Administrative Templates > Windows Components > Remote Desktop Services > Remote Desktop Session Host > Connections.
- Set Restrict Remote Desktop Services user to a single Remote Desktop Services session to Disabled.
- Double click Limit number of connections and set the RD Maximum Connections allowed to 999999.
```

## Disable Multiple RDP Sessions

```
- Log into the server, where the Remote Desktop Services are installed.
- Open the start screen (press the Windows key) and type gpedit.msc and open it.
- Go to Computer Configuration > Administrative Templates > Windows Components > Remote Desktop Services > Remote Desktop Session Host > Connections.
- Set Restrict Remote Desktop Services user to a single Remote Desktop Services session to Enabled.
```
