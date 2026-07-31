# Gestion de Windows Update avec le module PowerShell PSWindowsUpdate

## 📖 Description

**PSWindowsUpdate** est un module PowerShell permettant d'administrer Windows Update directement en ligne de commande.

Il permet notamment de :

- Rechercher les mises à jour disponibles.
- Installer ou masquer des mises à jour.
- Consulter l'historique Windows Update.
- Vérifier l'état d'un serveur WSUS.
- Réinitialiser les composants Windows Update.

Ce module est particulièrement utile pour le dépannage, l'administration de postes et les environnements avec WSUS.

---

## 📋 Prérequis

- Windows PowerShell lancé en administrateur.
- Accès Internet ou accès au serveur WSUS configuré.
- Module PowerShell Gallery disponible.

---

# ⚙️ Installation du module PSWindowsUpdate

Installer le module :

```powershell
Install-Module -Name PSWindowsUpdate -Force
```

L'option :

```text
-Force
```

permet de forcer l'installation ou la mise à jour du module.

---

# 🔍 Vérifier la configuration Windows Update / WSUS

Afficher la configuration actuelle :

```powershell
Get-WUSettings
```

Permet notamment d'obtenir :

- La présence d'un serveur WSUS.
- Les paramètres Windows Update.
- Les configurations appliquées au poste.

---

# 🔎 Rechercher les mises à jour disponibles

Lister les mises à jour disponibles :

```powershell
Get-WindowsUpdate
```

Affiche les mises à jour détectées par Windows Update.

---

# 📥 Installer les mises à jour

Installer toutes les mises à jour disponibles :

```powershell
Install-WindowsUpdate -AcceptAll
```

Paramètre utilisé :

```text
-AcceptAll
```

Accepte automatiquement les demandes de confirmation.

> [!IMPORTANT]
> Certaines mises à jour peuvent nécessiter un redémarrage du poste.

---

# 🔄 Vérifier si un redémarrage est nécessaire

Vérifier l'état du redémarrage :

```powershell
Get-WURebootStatus
```

Permet de savoir si Windows attend un redémarrage après l'installation de mises à jour.

---

# 📜 Consulter l'historique des mises à jour

Afficher les mises à jour installées :

```powershell
Get-WUHistory
```

Permet de consulter :

- Les KB installées.
- Les dates d'installation.
- Le résultat des installations.

---

# 🗑️ Désinstaller une mise à jour

Supprimer une mise à jour spécifique avec son identifiant KB :

```powershell
Remove-WindowsUpdate -KBArticleID "KB1234567"
```

Remplacer :

```text
KB1234567
```

par l'identifiant réel de la mise à jour.

Exemple :

```powershell
Remove-WindowsUpdate -KBArticleID "KB5039212"
```

---

# 🛠️ Réinitialiser complètement Windows Update

Réinitialiser les composants Windows Update :

```powershell
Reset-WUComponents -Verbose
```

Cette commande permet de réparer certains problèmes liés à Windows Update en :

- Réinitialisant les services Windows Update.
- Nettoyant les fichiers temporaires de mise à jour.
- Réinitialisant les composants associés.

> [!WARNING]
> Cette commande doit être utilisée uniquement en cas de problème Windows Update persistant.

---

# ✅ Vérification après intervention

Après une réparation ou installation :

Vérifier les mises à jour disponibles :

```powershell
Get-WindowsUpdate
```

Vérifier l'historique :

```powershell
Get-WUHistory
```

Vérifier si un redémarrage est nécessaire :

```powershell
Get-WURebootStatus
```

---

# 💡 Bonnes pratiques

- Tester les mises à jour sur un groupe pilote avant un déploiement massif.
- Vérifier l'espace disque disponible avant une mise à jour importante.
- Redémarrer les machines après les mises à jour critiques.
- Ne pas utiliser `Reset-WUComponents` en première intention : privilégier d'abord les diagnostics.

> [!TIP]
> Dans un environnement professionnel, ce module peut être utilisé avec des scripts PowerShell pour automatiser la maintenance d'un parc Windows.
