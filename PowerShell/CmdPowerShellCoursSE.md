# **Commande PowerShell du Cours 10 SE**

<mark>**Date : 16 mars 2021**</mark>

**Diapo 6**

```powershell
Pwsh –command Get-Date
Pwsh –NoExit –command Get-Date
pwsh – version
pwsh –WorkingDirectory C:\Windows
Pwsh /?
```

**Diapo 7**

```powershell
# Télécharger l’aide 
Update-Help (attention d’être administrateur)
Update-Help -UICulture en-us (l’aide française provoque un erreur)
Get-Help Get-date –Online
Get-Help Get-date -Example
Get-Help about_if
```

**Diapo 8**

```powershell
Get-Date; Get-Item c:\Windows
```

Diapo 10

```powershell
Get-Process
Get-Process | out-file  c:\ps\process.txt     
Get-Process | Select-Object name
Get-process | Select-Object name ?     (pour avoir plus d’une propriété.
Get-process | Select-Obect name | out-file  c:\ps\process.txt
clear-host
Get-Command 
Get-Command | out-host     (Pas nécessaire sauf si on veut des paramètre de la commande).
Get-Command | out-host -Paging
```

Diapo 12

```powershell
Clear ou Clear-Host
Get-psprovider
Get-PSDrive
Set-Location D:
Get-Item {tabulation} affiche les fichiers et dossiers
New-item –itemtype –Name test.txt
Get-item test.txt
```

Diapo 14

```powershell
Get-Service | Where-Object -Property Status -eq "Running“
Get-Service | Where-Object -Property Status -eq “Stopped“| out-file  c:\ps\process.txt
Get-childItem c:\windows
Get-Childitem c:\windows | Where-Object –Property Length -lt 1MB
Get-Service | Group-Object –Property Status
```

Diapo 15

```powershell
Get-Service | ForEach-Object { if ($_.Status -eq "Stopped"){"Service arrêté :  " + $_.Name} }
Pour faire un Else
Get-Service | ForEach-Object { if ($_.Status -eq "Stopped"){"Service arrêté :  " + $_.Name} }

Get-Help about_if
Get-Service | ForEach-Object { if ($_.Status -eq "Stopped"){"Service arrêté :  " + $_.Name} else {"Service en marche :  " + $_.Name} } > d:\EtatDesServices.txt
```

Diapo 18 Get-Member

```powershell
Get-ChildItem | Get-Member -MemberType Method 
Get-ChildItem | Get-Member -MemberType Method  | Measure-Object
Get-ChildItem | Get-Member -MemberType Properties | Measure-Object
# Récupérer une propriété :
(Get-ChildItem C:\Users\).CreationTime
(Get-ChildItem C:\Users\).CreationTime.ToShortDateString() (propriété et méthode) 
Get-Item -Path D:\etatService.txt
```

Diapo 19

```powershell
Get-ChildItem | Get-Member 
Get-ChildItem | Get-Member | Measure-Object

Get-Process | Get-Member -MemberType Method
Get-Process | Get-Member | Out-Host -Paging
Get-Process | Get-Member -MemberType Properties
Get-Process | Get-Member -MemberType Method
```

Diapo 20

```powershell
# Créer un fichier avec valeur :
New-Item -Path D:\ -Name test.txt -value "PowerShell"

# Récupérer une propriété :

(Get-ChildItem C:\Users\).CreationTime
(Get-ChildItem C:\Users\).CreationTime.ToShortDateString() (propriété et méthode) 
Get-Item -Path D:\etatService.txt
(Get-Item -Path D:\etatService.txt).Length
```
