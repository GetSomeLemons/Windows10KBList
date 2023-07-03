# Windows10KBList
.json list of KB's for Windows 10 from 20H1 to 22H2

## How to use with Powershell
You can either download the .json, or you can use it straight from GitHub:

```PowerShell
$jsonPath = 'https://raw.githubusercontent.com/GetSomeLemons/Windows10KBList/main/Windows10KBList.json'
$json = (New-Object System.Net.WebClient).DownloadString($jsonPath) | ConvertFrom-Json
```

After this, you most likely have to drill a little bit deeper into the .json file to get some information.

If you for example want to get KB articles for Windows 10 22H2, use this:

```PowerShell
$json.Windows10 | select 22H2 | % {$_.psobject.properties | % {$_.Value | % {$_.KBs | % {$_.psobject.properties | % {$_.Name}}}}}
```


**It is highly recommended that you understand Get-Member -functions role for digging deeper**

This is because PowerShell creates an object with ConvertFrom-Json -command.
