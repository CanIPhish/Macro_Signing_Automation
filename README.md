# Macro_Signing_Automation
Walkthrough of Microsoft's Office Macro Signing Utility

Setup Steps:
1. Download and install the [Windows 10 SDK](https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk) - ensure Microsoft Signing Tools for Desktop Applications is selected (everything else can be deselected)
2. Download and extract the Microsft [SIP Package](https://www.microsoft.com/en-us/download/confirmation.aspx?id=56617) to a folder of your choice (e.g. C:\SIP)
3. Register both the extracted msosip.dll and msosipx.dll files with regsvr32.exe on the local endpoint e.g.
  regsvr32.exe C:\SIP\msosip.dll
  regsvr32.exe C:\SIP\msosipx.dll
4. Add "C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86" to your System Path Environment Variables
5. Run signtool.exe with the appropriate parameters to cryptographically sign the intended Office Macro file e.g.
  signtool.exe sign /f "C:\Macro-Documents\certificate.pfx" /p "Password1234" /fd "SHA256" /tr "http://rfc3161timestamp.globalsign.com/advanced" /td "SHA256" "C:\Macro-Documents\sample.xlsm"
