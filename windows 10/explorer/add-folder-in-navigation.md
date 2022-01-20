Script allows you to add a folder to explorer navigation menu.<br/>
You need generate a GUID key by inserting `[guid]::NewGuid()` into the powershell or use [this site](https://www.guidgen.com/).

Replace `__PLACEHOLDER_GUID__` with your GUID key<br/>
Replace `__PLACEHOLDER_NAME__` with folder name<br/>
Replace `__PLACEHOLDER_PATH__` with path to folder (like `C:\\Windows`)

```
; set name
[HKEY_CURRENT_USER\Software\Classes\CLSID\{__PLACEHOLDER_GUID__}]
@="__PLACEHOLDER_NAME__"
"System.IsPinnedToNameSpaceTree"=dword:00000001

[HKEY_CURRENT_USER\Software\Classes\CLSID\{__PLACEHOLDER_GUID__}\Instance]
"CLSID"="{0E5AAE11-A475-4c5b-AB00-C66DE400274E}"

; set path
[HKEY_CURRENT_USER\Software\Classes\CLSID\{__PLACEHOLDER_GUID__}\Instance\InitPropertyBag]
"Attributes"=dword:00000011
"TargetFolderPath"="__PLACEHOLDER_PATH__"

[HKEY_CURRENT_USER\Software\Classes\CLSID\{__PLACEHOLDER_GUID__}\ShellFolder]
"FolderValueFlags"=dword:00000028
"Attributes"=dword:f080004d

[HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Desktop\NameSpace\{__PLACEHOLDER_GUID__}]

[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\HideDesktopIcons\NewStartPanel]
"{__PLACEHOLDER_GUID__}"=dword:00000001
```
> Confirmed to work on version 19044.1288
