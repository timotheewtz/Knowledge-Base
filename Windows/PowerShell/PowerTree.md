# Visualiser une arborescence de fichiers avec PowerTree

## 📖 Description

**PowerTree** est un module PowerShell permettant de représenter une structure de fichiers et dossiers sous forme d'arborescence.

Il fonctionne sur le même principe que la commande Windows native :

```cmd
tree
```

mais apporte des fonctionnalités supplémentaires :

- Affichage détaillé des dossiers et fichiers.
- Filtrage des éléments affichés.
- Affichage des tailles.
- Tri des résultats.
- Export des résultats.

PowerTree est particulièrement utile pour :

- Documenter une architecture de fichiers.
- Analyser une arborescence de stockage.
- Auditer un dossier avant migration.
- Visualiser rapidement une structure de projet.

---

## 📋 Prérequis

- PowerShell installé.
- Accès à PowerShell Gallery.
- Droits suffisants sur les dossiers à analyser.

> [!NOTE]
> Les versions récentes de PowerTree nécessitent PowerShell 7+. Certaines versions précédentes supportent PowerShell 5.1. :contentReference[oaicite:2]{index=2}

---

# ⚙️ Installation

Installer le module PowerTree depuis PowerShell Gallery :

```powershell
Install-Module -Name PowerTree
```

Pour forcer une installation ou une mise à jour :

```powershell
Install-Module -Name PowerTree -Force
```

---

# 🌳 Afficher une arborescence

Afficher l'arborescence du dossier courant :

```powershell
PowerTree
```

---

Afficher l'arborescence d'un chemin spécifique :

```powershell
PowerTree -Path "C:\Users"
```

Exemple :

```powershell
PowerTree -Path "C:\Projet"
```

Résultat :

```text
Projet
│
├── Documents
│   ├── Rapport.docx
│   └── Notes.txt
│
├── Scripts
│   └── Deploy.ps1
│
└── README.md
```

---

# 📊 Afficher les tailles des fichiers

Afficher la taille des éléments :

```powershell
PowerTree -DisplaySize
```

Permet d'identifier rapidement les dossiers ou fichiers volumineux.

---

# 🔍 Filtrer l'affichage

Exemple : afficher uniquement certains types de fichiers :

```powershell
PowerTree -IncludeExtensions ps1,md
```

Utile pour analyser :

- Scripts PowerShell.
- Documentation Markdown.
- Fichiers de configuration.

---

# 💾 Exporter le résultat

Exporter une arborescence dans un fichier texte :

```powershell
PowerTree > arbre.txt
```

Permet de conserver une représentation d'une structure de dossiers.

---

# 💡 Exemple d'utilisation

Créer une documentation d'un projet :

```powershell
PowerTree -Path "C:\Projet" -DisplaySize > structure-projet.txt
```

Le fichier généré peut ensuite être intégré dans une documentation technique.

---

# ✅ Bonnes pratiques

- Utiliser PowerTree avant une migration de données.
- Limiter l'analyse aux dossiers nécessaires pour éviter des sorties trop volumineuses.
- Exporter les résultats dans un fichier pour garder une trace.
- Vérifier les droits d'accès avant d'analyser des répertoires sensibles.

---

## 🔗 Alternatives natives Windows

Sans installation supplémentaire, Windows propose également :

```cmd
tree
```

Afficher les fichiers inclus :

```cmd
tree /F
```

Afficher l'arborescence avec les chemins en format ASCII :

```cmd
tree /A
```
