# **NLA (Network Level Authentication)** 

คือ ระบบรักษาความปลอดภัยขั้นแรกของการใช้งาน Remote Desktop (RDP) ใน Windows Server 2019 ที่บังคับให้ผู้ใช้งานต้อง **ยืนยันตัวตน (ใส่ Username และ Password) ให้ผ่านก่อน** ที่เซิร์ฟเวอร์จะยอมสร้างหน้าจอ Session (หน้าจอ Login ของ Windows) ให้

เพื่อทำความเข้าใจให้เห็นภาพชัดเจนขึ้น สามารถเปรียบเทียบการทำงานได้ดังนี้:

* **หากปิด NLA (ระบบเก่า):** เมื่อคุณกดรีโมทไปหาเซิร์ฟเวอร์ เซิร์ฟเวอร์จะจำลองหน้าจอ Login ของ Windows ขึ้นมาแสดงผลให้คุณเห็นทันทีเพื่อให้คุณพิมพ์รหัสผ่าน การทำแบบนี้เซิร์ฟเวอร์ต้องดึงทรัพยากร (CPU/RAM) มาสร้างหน้าจอรอไว้ ซึ่งเปิดโอกาสให้แฮกเกอร์โจมตีเพื่อทำให้เซิร์ฟเวอร์ค้าง (DoS Attack) ได้ง่าย
* **หากเปิด NLA:** หน้าต่างแจ้งให้ใส่รหัสผ่านจะเด้งขึ้นมาที่เครื่องต้นทางของคุณเอง หากคุณใส่รหัสผ่านไม่ถูกต้อง เซิร์ฟเวอร์จะปฏิเสธการเชื่อมต่อและตัดทิ้งทันที โดยยังไม่ได้ดึงทรัพยากรใดๆ ในเครื่องมาใช้เลย

**ข้อดีหลักของการเปิดใช้งาน NLA บน Windows Server 2019:**

* **ป้องกันการโจมตีแบบ DoS (Denial of Service):** ลดความเสี่ยงที่เซิร์ฟเวอร์จะล่มจากการถูกกระหน่ำขอเชื่อมต่อ Remote Desktop
* **ประหยัดทรัพยากรระบบ:** เซิร์ฟเวอร์ไม่ต้องสูญเสียหน่วยความจำไปกับการสร้าง Session ให้กับการเชื่อมต่อที่ยังไม่ได้รับอนุญาต
* **สกัดกั้นมัลแวร์และการเดารหัสผ่าน (Brute-force):** ป้องกันภัยคุกคามหรือช่องโหว่ระดับเครือข่ายที่พุ่งเป้ามาที่พอร์ต RDP ได้ตั้งแต่ด่านแรก

ใน Windows Server 2019 Standard โดยปกติแล้วเมื่อคุณเปิดฟีเจอร์ Remote Desktop ระบบจะติ๊กเลือกเปิดใช้งาน NLA มาให้เป็นค่าเริ่มต้น (Recommended) เพื่อความปลอดภัยสูงสุด

# การเปิดใช้งาน **Remote Desktop พร้อมบังคับใช้ NLA** 

บน Windows Server 2019 สามารถทำได้ผ่าน PowerShell หรือ Command Prompt (CMD) โดยต้องเปิดโปรแกรมด้วยสิทธิ์ผู้ดูแลระบบ (Run as Administrator)

**วิธีที่ 1: ผ่าน PowerShell (แนะนำ)**

```powershell
# 1. เปิดการเชื่อมต่อ Remote Desktop
Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server' -name "fDenyTSConnections" -value 0

# 2. เปิดการบังคับใช้ NLA (Network Level Authentication)
Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp' -name "UserAuthentication" -value 1

# 3. อนุญาตให้แพ็กเกจ Remote Desktop ผ่าน Windows Firewall ได้
Enable-NetFirewallRule -DisplayGroup "Remote Desktop"

```

**วิธีที่ 2: ผ่าน Command Prompt (CMD)**

```cmd
:: 1. เปิดการเชื่อมต่อ Remote Desktop
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server" /v fDenyTSConnections /t REG_DWORD /d 0 /f

:: 2. เปิดการบังคับใช้ NLA (Network Level Authentication)
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp" /v UserAuthentication /t REG_DWORD /d 1 /f

:: 3. อนุญาตให้แพ็กเกจ Remote Desktop ผ่าน Windows Firewall ได้
netsh advfirewall firewall set rule group="remote desktop" new enable=Yes

```
