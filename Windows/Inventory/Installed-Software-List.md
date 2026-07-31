# Lister les logiciels installés avec PowerShell

## 📖 Description

Windows possède une interface graphique permettant d'afficher les logiciels installés :

```text
Panneau de configuration
→ Programmes et fonctionnalités
```

ou via :

```cmd
appwiz.cpl
```

Cette commande PowerShell permet d'obtenir une liste similaire directement en ligne de commande.

Elle est utile pour :

- Réaliser un inventaire logiciel.
- Vérifier la présence d'un logiciel sur un poste.
- Préparer une migration ou un audit.
- Collecter des informations avant une intervention.

---

## ⚙️ Afficher les logiciels installés

Exécuter la commande suivante dans PowerShell :

```powershell
Get-ItemProperty HKLM:\Software\Wow6432Node\Microsoft\Windows\CurrentVersion\Uninstall\* |
Select-Object DisplayName, DisplayVersion, Publisher, InstallDate |
Where-Object { $_.DisplayName } |
Sort-Object DisplayName
```

---

## 🔎 Explication de la commande

### Récupération des logiciels installés

```powershell
Get-ItemProperty HKLM:\Software\Wow6432Node\Microsoft\Windows\CurrentVersion\Uninstall\*
```

Interroge la base de registre Windows contenant les informations des applications installées.

---

### Affichage des informations importantes

```powershell
Select-Object DisplayName, DisplayVersion, Publisher, InstallDate
```

Affiche :

| Champ          | Description         |
| -------------- | ------------------- |
| DisplayName    | Nom du logiciel     |
| DisplayVersion | Version installée   |
| Publisher      | Éditeur du logiciel |
| InstallDate    | Date d'installation |

---

### Suppression des entrées vides

```powershell
Where-Object { $_.DisplayName }
```

Ignore les entrées ne possédant pas de nom de logiciel.

---

### Tri alphabétique

```powershell
Sort-Object DisplayName
```

Classe les résultats par nom de logiciel.

---

# 💾 Exporter la liste des logiciels

Exporter le résultat dans un fichier CSV :

```powershell
Get-ItemProperty HKLM:\Software\Wow6432Node\Microsoft\Windows\CurrentVersion\Uninstall\* |
Select-Object DisplayName, DisplayVersion, Publisher, InstallDate |
Where-Object { $_.DisplayName } |
Sort-Object DisplayName |
Export-Csv "C:\Temp\Software-Inventory.csv" -NoTypeInformation -Encoding UTF8
```

Le fichier généré pourra être exploité dans :

- Excel.
- Un outil d'inventaire.
- Une documentation technique.

---

# ⚠️ Limitation

Cette commande interroge uniquement une partie du registre Windows.

Pour obtenir un inventaire plus complet, il est recommandé d'interroger également :

```text
HKLM:\Software\Microsoft\Windows\CurrentVersion\Uninstall\*
```

et la partie utilisateur :

```text
HKCU:\Software\Microsoft\Windows\CurrentVersion\Uninstall\*
```

---

# 💡 Alternative moderne

Pour obtenir les applications installées via Windows Package Manager :

```powershell
winget list
```

Cette commande affiche les applications détectées par Windows et peut être utilisée avec :

```text
winget upgrade
```

pour la gestion des mises à jour.

---

# 🛠️ Utilisation en environnement professionnel

Cette méthode peut être intégrée dans :

- Scripts PowerShell d'inventaire.
- Outils RMM.
- Solutions de gestion de parc.
- Audits logiciels.
