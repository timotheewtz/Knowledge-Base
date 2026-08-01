# Exemples de Group Policy Objects (GPO) et Group Policy Preferences (GPP)

## 📖 Description

Les **Group Policy Objects (GPO)** permettent d'appliquer automatiquement des paramètres de configuration aux ordinateurs et aux utilisateurs d'un domaine **Microsoft Active Directory**.

Deux grandes catégories sont utilisées :

- **Stratégies (Policies)** : paramètres imposés par Windows, généralement non modifiables par l'utilisateur.

- **Préférences (Group Policy Preferences - GPP)** : permettent de déployer des lecteurs réseau, raccourcis, fichiers, clés de registre, tâches planifiées, imprimantes, etc.

Cette fiche regroupe plusieurs exemples de GPO et GPP couramment utilisées en environnement professionnel.

---

# 📚 Sommaire

1. Désactiver la découverte réseau

2. Définir la page de démarrage Microsoft Edge

3. Mapper automatiquement un lecteur réseau personnel

4. Déployer un raccourci sur le Bureau

5. Déployer un fond d'écran d'entreprise

6. Déployer un agent SentinelOne

7. Déployer un agent FreshService

8. GPO complémentaires recommandées

9. Bonnes pratiques

---

# 🖥️ Désactiver la découverte réseau

## 🎯 Objectif

Masquer les ordinateurs voisins ainsi que l'ensemble du réseau dans l'Explorateur Windows.

## 📍 Emplacement

```text
Configuration utilisateur
└── Préférences
    └── Paramètres Windows
        └── Registre
```

## ⚙️ Configuration

| Paramètre     | Valeur                                     |
| ------------- | ------------------------------------------ |
| Action        | Mettre à jour                              |
| Ruche         | HKEY_CURRENT_USER                          |
| Clé           | SYSTEM\CurrentControlSet\Services\FDResPub |
| Nom de valeur | Start                                      |
| Type          | REG_DWORD                                  |
| Données       | 4 (Hexadécimal)                            |

Dans l'onglet **Commun**, cocher :

- ✅ Exécuter dans le contexte de sécurité de l'utilisateur connecté.

### Paramètres complémentaires

```text
Configuration utilisateur
└── Stratégies
    └── Modèles d'administration
        └── Tous les paramètres
```

Activer :

- Ne pas afficher **Ordinateurs proches** dans les emplacements réseau.

- Ne pas afficher **Tout le réseau** dans les emplacements réseau.

---

# 🌐 Définir la page de démarrage Microsoft Edge

## 🎯 Objectif

Configurer automatiquement la page d'accueil affichée au lancement de Microsoft Edge.

## 📍 Emplacement

```text
Configuration ordinateur
└── Préférences
    └── Paramètres Windows
        └── Registre
```

Créer les trois valeurs suivantes.

### RestoreOnStartupURLs

| Paramètre | Valeur                                                |
| --------- | ----------------------------------------------------- |
| Ruche     | HKLM                                                  |
| Clé       | SOFTWARE\Policies\Microsoft\Edge\RestoreOnStartupURLs |
| Nom       | 1                                                     |
| Type      | REG_SZ                                                |
| Données   | [https://www.google.com](https://www.google.com/)     |

### HomepageLocation

| Paramètre | Valeur                                            |
| --------- | ------------------------------------------------- |
| Ruche     | HKLM                                              |
| Clé       | SOFTWARE\Policies\Microsoft\Edge                  |
| Nom       | HomepageLocation                                  |
| Type      | REG_SZ                                            |
| Données   | [https://www.google.com](https://www.google.com/) |

### RestoreOnStartup

| Paramètre | Valeur                           |
| --------- | -------------------------------- |
| Ruche     | HKLM                             |
| Clé       | SOFTWARE\Policies\Microsoft\Edge |
| Nom       | RestoreOnStartup                 |
| Type      | REG_DWORD                        |
| Données   | 4                                |

---

# 📁 Mapper automatiquement un lecteur réseau personnel

## 🎯 Objectif

Créer automatiquement le dossier personnel de chaque utilisateur puis mapper un lecteur réseau.

## Création du dossier

```text
Configuration utilisateur
└── Préférences
    └── Paramètres Windows
        └── Dossiers
```

| Paramètre | Valeur                       |
| --------- | ---------------------------- |
| Action    | Mettre à jour                |
| Chemin    | \\Serveur\Partage\%USERNAME% |

Dans **Commun** :

- ✅ Exécuter dans le contexte de sécurité de l'utilisateur connecté.

## Mappage du lecteur

```text
Configuration utilisateur
└── Préférences
    └── Paramètres Windows
        └── Mappage de lecteurs
```

| Paramètre   | Valeur                       |
| ----------- | ---------------------------- |
| Action      | Mettre à jour                |
| Emplacement | \\Serveur\Partage\%USERNAME% |
| Lettre      | P:                           |
| Reconnecter | Oui                          |
| Affichage   | Afficher le lecteur          |

Dans **Commun** :

- ✅ Exécuter dans le contexte de sécurité de l'utilisateur connecté.

---

# 🖌️ Déployer un raccourci sur le Bureau

## 🎯 Objectif

Créer automatiquement un raccourci vers une application sur le Bureau des utilisateurs.

## 📍 Emplacement

```text
Configuration utilisateur
└── Préférences
    └── Paramètres Windows
        └── Raccourcis
```

Configuration recommandée :

| Paramètre     | Valeur                                           |
| ------------- | ------------------------------------------------ |
| Action        | Mettre à jour                                    |
| Emplacement   | Bureau                                           |
| Type de cible | Objet du système de fichiers                     |
| Cible         | %LOCALAPPDATA%\Microsoft\WindowsApps\mspaint.exe |
| Icône         | %SystemRoot%\System32\SHELL32.dll                |
| Index         | 141                                              |

---

# 🖼️ Déployer un fond d'écran

## 🎯 Objectif

Déployer automatiquement un fond d'écran d'entreprise.

## Étape 1 — Copier le fichier

```text
Configuration ordinateur
└── Préférences
    └── Paramètres Windows
        └── Fichiers
```

| Paramètre   | Valeur                                 |
| ----------- | -------------------------------------- |
| Action      | Créer                                  |
| Source      | \\Serveur\Wallpaper\wallpaper.png      |
| Destination | C:\Windows\Web\Wallpaper\wallpaper.png |

Dans **Commun** :

- ✅ Appliquer une seule fois.

## Étape 2 — Définir le fond d'écran

```text
Configuration utilisateur
└── Stratégies
    └── Modèles d'administration
        └── Bureau
```

Configurer :

| Paramètre    | Valeur                                 |
| ------------ | -------------------------------------- |
| Papier peint | C:\Windows\Web\Wallpaper\wallpaper.png |
| Style        | Centre (ou selon les besoins)          |

---

# 🛡️ Déployer un agent SentinelOne

## 🎯 Objectif

Installer automatiquement l'agent SentinelOne au démarrage des postes.

## Procédure

1. Télécharger le MSI.

2. Récupérer le Token.

3. Préparer le script Batch.

4. Créer le dossier :

```text
\\<Domaine>\SYSVOL\<Domaine>\Scripts\SentinelOne
```

5. Copier le script et le MSI.

6. Ouvrir :

```text
Configuration ordinateur
└── Stratégies
    └── Paramètres Windows
        └── Scripts (Démarrage)
```

7. Ajouter le script Batch.

> [!TIP]  
> Vérifier les variables du script ainsi que les chemins UNC avant le déploiement.

---

# 🖥️ Déployer un agent FreshService

## 🎯 Objectif

Installer automatiquement l'agent FreshService via une GPO.

## Procédure

1. Télécharger le MSI.

2. Télécharger le script VBS fourni par FreshService.

3. Récupérer le Token.

4. Créer le dossier :

```text
\\<Domaine>\SYSVOL\<Domaine>\Scripts\FreshService
```

5. Copier le MSI et le script.

6. Ajouter le script dans :

```text
Configuration ordinateur
└── Stratégies
    └── Paramètres Windows
        └── Scripts (Démarrage)
```

7. Dans les paramètres du script, renseigner :
- Le chemin UNC du fichier MSI.

- Le Token d'installation.

---

# ⭐ GPO complémentaires recommandées

Parmi les GPO les plus couramment déployées en entreprise :

- Déployer une imprimante réseau.

- Déployer un proxy.

- Déployer un certificat.

- Configurer Microsoft Edge ou Google Chrome.

- Déployer un logiciel MSI.

- Configurer Windows Update (WSUS).

- Configurer le Pare-feu Windows.

- Déployer des variables d'environnement.

- Désactiver le Panneau de configuration.

- Définir la politique de mot de passe.

- Déployer des tâches planifiées.

- Copier automatiquement des fichiers de configuration.

---

# 💡 Bonnes pratiques

- Toujours tester une GPO sur une OU de validation avant un déploiement global.

- Éviter de modifier directement la **Default Domain Policy** ou la **Default Domain Controllers Policy** pour des besoins spécifiques.

- Nommer les GPO de manière explicite (ex. : `GPO - Déploiement SentinelOne`).

- Privilégier les **Group Policy Preferences** pour les lecteurs réseau, raccourcis, fichiers et clés de registre.

- Documenter chaque GPO (objectif, périmètre, date de création et auteur).

- Limiter l'utilisation des filtres WMI lorsque cela est possible afin de préserver les performances.

- Vérifier l'application des stratégies avec `gpresult`, `rsop.msc` ou la console **Group Policy Results**.

## 📚 Outils utiles

| Outil                      | Description                                           |
| -------------------------- | ----------------------------------------------------- |
| `gpupdate /force`          | Forcer l'application des GPO                          |
| `gpresult /r`              | Afficher les GPO appliquées                           |
| `gpresult /h rapport.html` | Générer un rapport HTML                               |
| `rsop.msc`                 | Afficher le jeu de stratégies résultant               |
| `gpmc.msc`                 | Ouvrir la console de gestion des stratégies de groupe |
| `dsa.msc`                  | Ouvrir Utilisateurs et ordinateurs Active Directory   |
| `eventvwr.msc`             | Consulter les journaux liés aux GPO                   |
