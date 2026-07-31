# Mise à jour des pilotes Dell avec Dell Command | Update

## 📖 Description

**Dell Command | Update (DCU)** est un outil Dell permettant d'automatiser la recherche et l'installation des mises à jour matérielles sur les postes Dell.

Il permet notamment de mettre à jour :

- Les pilotes matériels.
- Le BIOS.
- Les firmwares.
- Les applications Dell.
- Les composants liés au matériel.

Cet outil est particulièrement utile dans un environnement professionnel afin de maintenir un parc Dell homogène et à jour.

---

## 📋 Prérequis

- Poste Dell compatible.
- **Dell Command | Update** installé.
- Droits administrateur local.
- Alimentation secteur recommandée lors des mises à jour BIOS/firmware.

---

## 📂 Accéder au répertoire Dell Command | Update

Ouvrir PowerShell en administrateur puis accéder au dossier d'installation :

```powershell
cd "C:\Program Files\Dell\CommandUpdate"
```

---

# 🔍 Rechercher les mises à jour disponibles

Lancer une analyse du poste :

```powershell
.\dcu-cli.exe /scan
```

Cette commande recherche les mises à jour disponibles pour :

- Le BIOS.
- Les pilotes.
- Les firmwares.
- Les logiciels Dell.

---

# ⚙️ Installer les mises à jour disponibles

Appliquer les mises à jour détectées :

```powershell
.\dcu-cli.exe /applyUpdates
```

Cette commande installe automatiquement les mises à jour disponibles.

> [!IMPORTANT]
> Certaines mises à jour peuvent nécessiter un redémarrage du poste, notamment les mises à jour BIOS et firmware.

---

# 🔍 Vérification

Après l'installation :

- Redémarrer le poste si nécessaire.
- Relancer une analyse :

```powershell
.\dcu-cli.exe /scan
```

- Vérifier qu'aucune mise à jour critique n'est encore disponible.

---

# 💡 Bonnes pratiques

- Effectuer les mises à jour BIOS uniquement avec une alimentation secteur.
- Tester les mises à jour sur un groupe pilote avant un déploiement massif.
- Utiliser Dell Command | Update dans les scripts de maintenance ou outils de gestion de parc.

---

## 🚀 Déploiement automatisé

Dell Command | Update peut être intégré dans :

- Scripts PowerShell.
- GPO.
- Intune.
- Solutions RMM.
- Outils de gestion de parc.

Exemple d'organisation dans une base de scripts :

```text
Scripts
└── Hardware
    └── Dell
        └── Update-Drivers.ps1
```
