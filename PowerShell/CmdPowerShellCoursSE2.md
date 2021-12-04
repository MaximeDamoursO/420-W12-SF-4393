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

Get-Process | Get-Member 
Get-Process | Sort-Object -Property PM, PM -Descending | out-host -Paging

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

Diapo 11 Variables

```powershell
Clear-Host
$test = "PowerShell"
write-host $test

#1 Bonne façon de faire appel à la variable:
Write-Host " $test "  #Oui
Write-Host $test    #Oui
Write-Host '$test'  #On récupère selement son nom


#2 - Construite une chaine (concaténation)
Write-Host "La variable test possède $test.Length caractères" #Non
Write-Host "La variable test possède "$test.Length "caractères"
Write-Host "La variable test possède $($test.Length) caractères" #Méthode recommandée

# Récupérer les prorpiétés et les méthodes:
$test  |Get-Member


Write-host $test.ToUpper()
$test = $test.Replace('Power','Super')
$test.Length
Write-Host "La variable test possède : $($Test.Length) caractères"

$test.Replace("Power","Super" )
# Attention on a changé le contenu mais pas la variable.
# Preuve : 
Write-Host $test

# Mais ceci fait le travail : 
$test = $test.Replace("Power","Super" )
Write-Host $test

# Utilisation d'une propriétés : 
$test.Length

$Date = Get-Date
write-host $Date

# Here-String (Une très longue chaine)
$TextLong = @"

Ceci est un texte $Date

        sur 
        plusiers 

        ligne
"@

Write-Host $TextLong

```

Diapo 12 Incrémentation 

```powershell
$vitesse = 0
Write-Host "$vitesse"
$vitesse++
Write-Host $vitesse

$vitesse +=5
Write-Host $vitesse

$vitesse = 10
$vitesse --
write-host $vitesse
$vitesse -=3
write-host $vitesse
```


Diapo 13 Fonction simple 

```powershell
# Fonction simple 
function Recupere-DateCourte
{
    (Get-Date).ToShortDateString()
}
Recupere-DateCourte

# Avec paramètre
function envoiprocess-versfichier
{
    param([string]$chemin)
    Get-Process |Out-File $chemin
}
envoiprocess-versfichier  -chemin D:\PowerShell\process.txt
```

Diapo 13B Porté des variable

```powershell
#Portée des variables dans powerShell
$ville = "Québec"
function test
{
    write-host $ville
    $pays = "Canada"
    write-host $ville $pays
 }

write-host $ville
test
write-host $pays
```

Diapo 14 Écrire un fichier

```powershell
# Voici un exemple pour rediriger le résultat d'une commande, ici Dir, dans un fichier
Dir | Out-File "C:\MonFichierDir.txt"
dir > "C:\MonFichierDir.txt"
#Exporter un résultat dans un fichier csv
Get-Process | Export-csv -path D:\PowerShell\Export.csv -NoTypeInformation

#Pour écrire dans le fichier on utilise ADD-content

ADD-content -path "D:\Fichier_de_test.txt" -value "Test d'écriture"
```

Diapo 15 Lire un fichier

```powershell
Clear-Host

$EmplacementFichier = [string]

$EmplacementFichier = "./MonFichierALire.txt"
$MonFichier = Get-Content $emplacementFichier

foreach ($UneLigne in $MonFichier){
	Write-Host $UneLigne
}
```


Diapo 16 Boucle

```powershell
$valeur = 0..10
For($i=0 ; $i -lt 10 ; $i++) 
{ 
   Write-Output "La valeur est $($valeur[$i])" 
}
```

Diapo 17 Usagers

```powershell
Get-LocalUser
Get-LocalUser -name etudiant |Select-Object *

Get-LocalUser -name etudiant |Select-Object name, fullName, LastLogon
Get-LocalUser -Name * | Select-Object name, fullName, LastLogon


# Script de création d'un usager local avec les droits administrateurs
# Version 1.0
# Auteur [Votre nom]
# Date

# Création et affectation des variables
$nomUsager = "usager1"
$nomComplet = "Usager test"
$dateExpires = (get-date).AddYears(1)
$Description = "Test avec PowerShell"
$motPasse ="Soleil01"
$groupe = "Administrateurs"

New-LocalUser -Name $nomUsager -AccountExpires $dateExpires  -Description $Description -FullName $nomComplet -NoPassword
Add-LocalGroupMember -name $groupe -Member $nomUsager

```