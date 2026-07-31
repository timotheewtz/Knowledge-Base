# Gestion des logiciels avec Winget

## 📖 Description

**Winget** (Windows Package Manager) est le gestionnaire de paquets officiel de Microsoft. Il permet d'installer, mettre à jour, rechercher et désinstaller des logiciels directement depuis la ligne de commande.

> [!NOTE]
> Winget est intégré nativement à Windows 10 (versions récentes) et Windows 11.

---

## 📋 Prérequis

- Windows 10 ou Windows 11
- Winget installé (inclus avec **App Installer**)
- Une connexion Internet
- Ouvrir PowerShell ou Windows Terminal (de préférence en tant qu'administrateur)

---

## ⚙️ Rechercher les mises à jour disponibles

```powershell
winget update
```

Affiche la liste des logiciels pour lesquels une mise à jour est disponible.

---

## ⚙️ Installer toutes les mises à jour

```powershell
winget update --all
```

Met à jour automatiquement tous les logiciels détectés par Winget.

> [!TIP]
> Cette commande est idéale pour maintenir rapidement un poste Windows à jour.

---

## ⚙️ Forcer une mise à jour plus complète

```powershell
winget update --include-unknown --all
```

Met à jour tous les logiciels, y compris ceux dont la version installée n'a pas pu être déterminée.

Cette commande permet notamment de réinstaller ou mettre à jour certains composants comme :

- Microsoft Visual C++
- Microsoft Edge
- Microsoft Teams
- Microsoft PowerToys
- et d'autres applications dont la version est inconnue.

> [!IMPORTANT]
> Certains logiciels peuvent demander une fermeture préalable avant leur mise à jour.

---

## 🔍 Commandes utiles

### Rechercher un logiciel

```powershell
winget search firefox
```

---

### Installer un logiciel

```powershell
winget install Mozilla.Firefox
```

---

### Désinstaller un logiciel

```powershell
winget uninstall Mozilla.Firefox
```

---

### Afficher les logiciels installés

```powershell
winget list
```

---

## ✅ Vérification

Après une mise à jour, vérifier qu'aucune mise à jour n'est encore disponible :

```powershell
winget update
```

Si aucun logiciel n'est affiché, l'ensemble des applications gérées par Winget est à jour.

---

## 💡 Bonnes pratiques

- Exécuter régulièrement `winget update --all`.
- Utiliser Windows Terminal pour une meilleure expérience.
- Lancer PowerShell en tant qu'administrateur pour éviter les problèmes de permissions.
- Compléter les mises à jour Winget avec Windows Update afin de maintenir le système entièrement à jour.
