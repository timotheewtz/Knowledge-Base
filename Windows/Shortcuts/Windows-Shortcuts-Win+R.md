# Commandes Windows "Exécuter" (Win + R)

## 📖 Description

La fenêtre **Exécuter** (`Win + R`) permet d'ouvrir rapidement des outils d'administration, des consoles MMC, des panneaux de configuration ou des utilitaires Windows sans passer par les menus.

Cette fonctionnalité est particulièrement utile pour les administrateurs système et les techniciens de support.

---

## 🚀 Ouvrir la fenêtre Exécuter

Utiliser le raccourci clavier :

```text
Win + R
```

Une fenêtre s'ouvre permettant de saisir directement une commande.

---

# 🌐 Réseau

| Commande                 | Description                       |
| ------------------------ | --------------------------------- |
| `ncpa.cpl`               | Ouvrir les connexions réseau      |
| `control netconnections` | Ouvrir les connexions réseau      |
| `mstsc`                  | Connexion Bureau à distance (RDP) |
| `firewall.cpl`           | Pare-feu Windows Defender         |
| `cmd`                    | Invite de commandes               |
| `powershell`             | Windows PowerShell                |

---

# ⚙️ Administration système

| Commande       | Description                                            |
| -------------- | ------------------------------------------------------ |
| `services.msc` | Gestion des services Windows                           |
| `msconfig`     | Configuration du système                               |
| `taskmgr`      | Gestionnaire des tâches                                |
| `regedit`      | Éditeur du Registre                                    |
| `eventvwr.msc` | Observateur d'événements                               |
| `compmgmt.msc` | Gestion de l'ordinateur                                |
| `devmgmt.msc`  | Gestionnaire de périphériques                          |
| `perfmon`      | Moniteur de performances                               |
| `gpedit.msc`   | Éditeur de stratégie de groupe locale (Pro/Entreprise) |

---

# 🖥️ Panneau de configuration

| Commande       | Description                   |
| -------------- | ----------------------------- |
| `control`      | Panneau de configuration      |
| `appwiz.cpl`   | Programmes et fonctionnalités |
| `sysdm.cpl`    | Propriétés système            |
| `timedate.cpl` | Date et heure                 |
| `desk.cpl`     | Paramètres d'affichage        |
| `main.cpl`     | Paramètres de la souris       |
| `inetcpl.cpl`  | Options Internet              |
| `powercfg.cpl` | Options d'alimentation        |

---

# 🏢 Active Directory

| Commande       | Description                                        |
| -------------- | -------------------------------------------------- |
| `dsa.msc`      | Utilisateurs et ordinateurs Active Directory       |
| `dssite.msc`   | Sites et services Active Directory                 |
| `domain.msc`   | Domaines et approbations Active Directory          |
| `adsiedit.msc` | Éditeur ADSI                                       |
| `gpmc.msc`     | Console de gestion des stratégies de groupe (GPMC) |

> [!NOTE]
> Les outils Active Directory nécessitent généralement l'installation des **RSAT (Remote Server Administration Tools)** sur un poste client.

---

# 📂 Gestion des disques

| Commande       | Description                                   |
| -------------- | --------------------------------------------- |
| `diskmgmt.msc` | Gestion des disques                           |
| `diskpart`     | Outil de partitionnement en ligne de commande |
| `cleanmgr`     | Nettoyage de disque                           |

---

# 👤 Comptes utilisateurs

| Commande                 | Description                              |
| ------------------------ | ---------------------------------------- |
| `lusrmgr.msc`            | Utilisateurs et groupes locaux (Pro)     |
| `netplwiz`               | Gestion avancée des comptes utilisateurs |
| `control userpasswords2` | Gestion des comptes utilisateurs         |
| `passwords2`             | Alias de `control userpasswords2`        |

---

# 🔐 Sécurité

| Commande      | Description                                                  |
| ------------- | ------------------------------------------------------------ |
| `secpol.msc`  | Stratégie de sécurité locale                                 |
| `wf.msc`      | Pare-feu Windows Defender avec fonctions avancées            |
| `certmgr.msc` | Certificats de l'utilisateur                                 |
| `certlm.msc`  | Certificats de l'ordinateur local                            |
| `credwiz`     | Sauvegarde et restauration des informations d'identification |

---

# 📊 Journaux et diagnostic

| Commande       | Description                            |
| -------------- | -------------------------------------- |
| `resmon`       | Moniteur de ressources                 |
| `perfmon`      | Moniteur de performances               |
| `eventvwr.msc` | Observateur d'événements               |
| `dxdiag`       | Outil de diagnostic DirectX            |
| `msinfo32`     | Informations système                   |
| `winver`       | Version de Windows                     |
| `sigverif`     | Vérification des signatures numériques |

---

# 🌍 Réseau et Internet

| Commande           | Description             |
| ------------------ | ----------------------- |
| `ncpa.cpl`         | Cartes réseau           |
| `inetcpl.cpl`      | Options Internet        |
| `firewall.cpl`     | Pare-feu Windows        |
| `wf.msc`           | Pare-feu avancé         |
| `optionalfeatures` | Fonctionnalités Windows |

---

# 🧰 Outils système

| Commande           | Description                   |
| ------------------ | ----------------------------- |
| `optionalfeatures` | Fonctionnalités Windows       |
| `fsmgmt.msc`       | Dossiers partagés             |
| `compmgmt.msc`     | Gestion de l'ordinateur       |
| `services.msc`     | Services Windows              |
| `gpedit.msc`       | Stratégies locales            |
| `taskschd.msc`     | Planificateur de tâches       |
| `devmgmt.msc`      | Gestionnaire de périphériques |

---

# 📦 Outils Microsoft Management Console (MMC)

Les consoles **.msc** sont les principaux outils d'administration Windows.

Les plus utilisées sont :

| Console        | Description                   |
| -------------- | ----------------------------- |
| `compmgmt.msc` | Gestion de l'ordinateur       |
| `services.msc` | Services                      |
| `eventvwr.msc` | Journaux Windows              |
| `diskmgmt.msc` | Gestion des disques           |
| `devmgmt.msc`  | Gestionnaire de périphériques |
| `taskschd.msc` | Planificateur de tâches       |
| `gpmc.msc`     | Gestion des GPO               |
| `gpedit.msc`   | Stratégies locales            |
| `dsa.msc`      | Active Directory              |
| `secpol.msc`   | Stratégies de sécurité        |
| `lusrmgr.msc`  | Utilisateurs locaux           |

---

# 💡 Bonnes pratiques

- Privilégier les commandes **.msc** pour accéder rapidement aux consoles d'administration.
- Les commandes `.cpl` ouvrent directement les applets du Panneau de configuration.
- Les outils RSAT sont nécessaires pour les consoles Active Directory sur un poste client.
- Certaines commandes sont disponibles uniquement sur les éditions **Professionnel**, **Entreprise** ou **Server**.

## 📚 Les commandes les plus utilisées

| Commande       | Utilisation                   |
| -------------- | ----------------------------- |
| `cmd`          | Invite de commandes           |
| `powershell`   | Windows PowerShell            |
| `services.msc` | Services                      |
| `taskmgr`      | Gestionnaire des tâches       |
| `eventvwr.msc` | Journaux Windows              |
| `compmgmt.msc` | Gestion de l'ordinateur       |
| `devmgmt.msc`  | Gestionnaire de périphériques |
| `diskmgmt.msc` | Gestion des disques           |
| `ncpa.cpl`     | Cartes réseau                 |
| `appwiz.cpl`   | Désinstaller un programme     |
| `sysdm.cpl`    | Propriétés système            |
| `mstsc`        | Bureau à distance             |
| `gpmc.msc`     | Gestion des GPO               |
| `dsa.msc`      | Active Directory              |
| `winver`       | Version de Windows            |
| `msinfo32`     | Informations système          |
