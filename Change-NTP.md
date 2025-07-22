# Change the **time server host** and **synchronize time** 

**Windows 11 Home** using Command Prompt (CMD), follow these steps:

---

### 🛠️ 1. Change the Time Server (NTP Host)

To set a new time server (e.g., `time.windows.com`, `pool.ntp.org`, or your preferred NTP server):

```cmd
w32tm /config /manualpeerlist:"pool.ntp.org" /syncfromflags:manual /update
```

* Replace `pool.ntp.org` with your desired NTP server.
* `syncfromflags:manual` ensures it uses only the server(s) you've specified.

---

### 🔄 2. Force Synchronization with the Time Server

After setting the server, run:

```cmd
w32tm /resync
```

* This forces an immediate sync with the specified server.

> ⚠️ If you get an error like *"The service has not been started"*, start the Windows Time service manually:

```cmd
net start w32time
```

Then retry `w32tm /resync`.

---

### 🧾 3. Optional: Check Current Time Configuration

To verify your time settings:

```cmd
w32tm /query /configuration
```

To check the current time source:

```cmd
w32tm /query /status
```

---

Let me know if you want to do this via PowerShell or need to set it for multiple PCs in a network!
