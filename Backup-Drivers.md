To export all third-party (non-Microsoft) drivers from a Windows 10 system to a specific directory such as `C:\001`, you can use the `PnPUtil` or `DISM` command-line tools. The most common method is with `DISM`.

### ✅ Use `DISM` to Export Drivers

Open **Command Prompt as Administrator**, then run:

```cmd
dism /online /export-driver /destination:"C:\001"
```

### 📌 Notes:

* `dism /online`: Works on the current running Windows installation.
* `/export-driver`: Exports all third-party drivers from the DriverStore.
* `/destination`: Specifies the folder to store the exported `.inf`, `.sys`, and associated files.

If the folder `C:\001` does not exist, DISM will create it automatically.

Let me know if you want to filter specific drivers or use PowerShell instead.
