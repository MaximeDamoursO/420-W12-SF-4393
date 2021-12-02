# **Commande PowerShell du Cours SE**

<mark>**Date : 16 mars 2021**</mark>

<mark>**Update : 2 décembre 2021**</mark>


**Tapez ces commandes dans la barre de recherche Windows**

```powershell
Pwsh –command Get-Date
Pwsh –NoExit –command Get-Date
pwsh – version
pwsh –WorkingDirectory C:\Windows
Pwsh /?
```
**Pour les prochaine diapo, tapez ces commandes dans PowerShell**

**Diapo 4**

```powershell
# Télécharger l’aide 
Get-Help Get-Date
Get-Help Get-Date –Online
Get-Help Get-Date -Example
Get-Help about_if
```

**Diapo 5**

```powershell
Get-Date; Get-Item c:\Windows
```

Diapo 7

```powershell
Get-Process
Get-Process | out-file  c:\ps\process.txt #Envoyer le résultat dans un fichier texte.
Get-Process | Select-Object name #Récupérer seulement le nom des processes.

Get-process | Select-Obect name | out-file  c:\ps\process.txt
clear-host
Get-Command 
Get-Command | out-host  # (C'est la sortie par défaut. Donc pas nécessaire sauf si on veut des paramètres de la commande comme ce qui suit :).
Get-Command | out-host -Paging
```
Diapo 10
Exemple  de cmdlet à maitriser!

```powershell
help *process*
Get-Help processes 
Get-Command -Name *service*
Get-Service | Get-Member | Out-GridView
![image](https://user-images.githubusercontent.com/78882425/144509069-0cb23ab1-7b3d-4357-ac19-2d945c73a6f5.png)

```
## Deuxième cours Lundi le 6 décembre
Diapo 13

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
