
# Multiple RDP

## run => gpedit.msc

```
Computer Configuration\Administrative Templates\Windows Components\Remote Desktop Services\ Remote Desktop Session Host\Connections\
```

### Restrict Remote Desktop Services users to a single Remote Desktop Services session

```
Value: Disabled
```

### Limit number of connections

```
set the RD Maximum Connections allowed to 999999.
```

## Or you could edit the registry as follows:

### HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server


```
fSingleSessionPerUser value: 0
```

```
fdenyTSConnections value: 0
```

### OPEN PowerShell RUN as administrator

```
# Reapply all policies
gpupdate /force

# Get only the changed / new group policies
gpupdate
```
