Windows does **not provide a built-in command** to directly show saved passwords for **Remote Desktop (RDP)** sessions due to security reasons. However, I can show you several ways to **retrieve or view saved RDP credentials** depending on how they were stored.

---

### 🔐 1. **Using Credential Manager (GUI)**
You can view stored credentials manually:

1. Press `Win + R` → type `control /name Microsoft.CredentialManager` → hit Enter.
2. Look under **"Windows Credentials"**.
3. Find entries like `TERMSRV/<hostname or IP>`.
4. Click the entry to view the saved username.  
   🔒 **Password is not shown**, but you can remove or edit the credential.

---

### 💻 2. **Using Command Line: `cmdkey`**
To **list saved credentials** for RDP:

```cmd
cmdkey /list
```

You’ll see entries like:

```
Target: TERMSRV/192.168.1.10
Type: Domain Password
User: your_username
```

🔒 Again, the **password is not shown**, only the username and target.

---

### 🛠️ 3. **Using PowerShell (read-only info)**
This PowerShell command will also list RDP credentials stored:

```powershell
cmdkey /list | Select-String "TERMSRV"
```

---

### 🚫 4. **Can You Extract the Password?**
- **No official way.** Windows encrypts credentials using DPAPI.
- There are **third-party tools** like **Mimikatz** or **NirSoft's Network Password Recovery**, but:
  - ⚠️ These may trigger antivirus alerts.
  - ❌ Not legal or ethical to use on systems you don’t own/administer.
  - ❗ Use responsibly and only on your own machines for recovery purposes.

---

Would you like help with a safe way to clear, update, or manage RDP credentials?
