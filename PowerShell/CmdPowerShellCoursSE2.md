# **Commande PowerShell du Cours SE**

<mark>**Date : 4 décembre 2021**</mark>



**Pour les prochaine diapo, tapez ces commandes dans PowerShell**

**Diapo 4**

Exemple  de cmdlet à maitriser!

```powershell
help *process*
Get-Help processes 
Get-Command -Name *service*

#One-liners (Utilisation d'une seule commande sur une ligne)
Get-Service |
  Where-Object CanPauseAndContinue -eq $true |
    Select-Object -Property *

# Analysez la réponse. Vérifiez le propriété CanPauseAndContinue.
# A quoi sert le Select-Object -Property *
```

**Diapo 5**

Personnaliezer la sortie d'une cmdlet simple

```powershell
Clear ou Clear_host
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer’
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
# Vous pouvez utiliser le paramètre Width pour spécifier une largeur de ligne. 
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647

Get-Process | Out-File -FilePath C:\temp\processlist.txt
Get-Command  |Out-Null

```


Diapo 6
Retour sur les provider et PSDrives

```powershell
Clear ou Clear_host

Get-psprovider
Get-PSDrive
New-PSDrive SE filesystem 'D:\OneDrive - Cégep de Sainte-Foy\Cours\420-W12-SF-4392\'
cd SE:
Dir or get-childitem
cd c:	
remove-psdrive test
```

Diapo 8  Notion d'objet

```powershell
# Attention : utilisez une adresse valide sur votre système.
New-Item -Path D:\ -Name test.txt -value "PowerShell"

Récupérer une propriété :

(Get-ChildItem D:\test.txt).CreationTime
(Get-ChildItem C:\Users\).CreationTime.ToShortDateString() #(propriété et méthode) 
# Attention le fichier doit exsiter
Get-Item -Path D:\etatService.txt
(Get-Item -Path D:\etatService.txt).Length

```

Diapo 9 Get-Member

```powershell
Get-ChildItem | Get-Member -MemberType Method 
Get-ChildItem | Get-Member -MemberType Method  | Measure-Object
Get-ChildItem | Get-Member -MemberType Properties | Measure-Object
# Récupérer une propriété :
(Get-ChildItem C:\Users\).CreationTime
(Get-ChildItem C:\Users\).CreationTime.ToShortDateString() # (propriété et méthode) 

Get-Item -Path D:\etatService.txt
Get-ChildItem | Get-Member 
Get-ChildItem | Get-Member | Measure-Object
Get-Process | Get-Member -MemberType Method
Get-Process | Get-Member | Out-Host -Paging
Get-Process | Get-Member -MemberType Properties

```
