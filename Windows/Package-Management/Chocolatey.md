# Installation et utilisation de Chocolatey

## 📖 Description

**Chocolatey** est un gestionnaire de paquets pour Windows permettant d'installer, mettre à jour et désinstaller des logiciels depuis la ligne de commande.

Il fonctionne sur le même principe que des gestionnaires de paquets Linux comme **APT** (`apt install`) ou **YUM** (`yum install`).

Chocolatey permet notamment de :

- Automatiser l'installation de logiciels.
- Déployer rapidement des outils sur plusieurs machines.
- Maintenir les applications à jour.
- Standardiser les installations dans un environnement professionnel.

Exemples de logiciels disponibles :

- Google Chrome
- Mozilla Firefox
- 7-Zip
- Git
- Visual Studio Code
- Docker Desktop
- PowerShell

---

## 📋 Prérequis

- Windows 7 ou version supérieure.
- PowerShell 5 ou supérieur.
- Console PowerShell ouverte en administrateur.
- Connexion Internet.

---

## ⚙️ Installation de Chocolatey

Exécuter la commande suivante dans une console PowerShell administrateur :

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

Cette commande :

1. Autorise temporairement l'exécution de scripts PowerShell pour la session actuelle.
2. Télécharge le script d'installation depuis le site officiel Chocolatey.
3. Exécute automatiquement l'installation du gestionnaire de paquets.

> [!IMPORTANT]
> Toujours vérifier la provenance d'un script téléchargé et exécuté directement depuis Internet avant utilisation dans un environnement professionnel.

---

## 🔍 Vérifier l'installation

Vérifier que Chocolatey est correctement installé :

```powershell
choco --version
```

Retour attendu :

```text
2.x.x
```

---

## ⚙️ Commandes courantes

### Rechercher un logiciel

```powershell
choco search <nom_logiciel>
```

Exemple :

```powershell
choco search firefox
```

---

### Installer un logiciel

```powershell
choco install <nom_logiciel> -y
```

Exemple :

```powershell
choco install googlechrome -y
```

L'option :

```text
-y
```

permet d'accepter automatiquement les demandes de confirmation.

---

### Mettre à jour un logiciel

```powershell
choco upgrade <nom_logiciel> -y
```

Exemple :

```powershell
choco upgrade git -y
```

---

### Mettre à jour tous les logiciels installés via Chocolatey

```powershell
choco upgrade all -y
```

---

### Lister les logiciels installés

```powershell
choco list --local-only
```

---

### Désinstaller un logiciel

```powershell
choco uninstall <nom_logiciel> -y
```

---

## ✅ Vérification

Après installation d'un logiciel :

```powershell
choco list --local-only
```

Vérifier que le paquet apparaît bien dans la liste des applications gérées par Chocolatey.

---

## 💡 Bonnes pratiques

- Utiliser Chocolatey pour automatiser les installations sur des postes de test ou des environnements maîtrisés.
- Préférer les packages officiels ou vérifiés.
- Utiliser l'option `-y` dans les scripts d'automatisation.
- Vérifier régulièrement les mises à jour disponibles :

```powershell
choco outdated
```

> [!TIP]
> Dans un environnement d'entreprise, Chocolatey peut être couplé à des outils de gestion de parc (Intune, SCCM, scripts PowerShell...) afin d'automatiser le déploiement de logiciels.
