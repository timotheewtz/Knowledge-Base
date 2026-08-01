# Gestion des paquets avec APT

## 📖 Description

**APT (Advanced Package Tool)** est le gestionnaire de paquets utilisé par les distributions Linux basées sur **Debian**, telles que **Ubuntu**, **Linux Mint** ou encore **Kali Linux**.

Il permet notamment de :

- Rechercher des logiciels.

- Installer ou supprimer des paquets.

- Mettre à jour la liste des paquets disponibles.

- Mettre à niveau les logiciels installés.

- Gérer les dépendances automatiquement.

---

## 📋 Prérequis

- Distribution basée sur Debian.

- Accès à un compte disposant des droits `sudo`.

- Connexion Internet pour télécharger les paquets.

---

# 🔄 Mettre à jour la liste des paquets

Télécharger la liste des dernières versions disponibles :

```bash
sudo apt update
```

ou avec l'ancienne syntaxe :

```bash
sudo apt-get update
```

> [!NOTE]  
> Cette commande **n'installe aucune mise à jour**. Elle actualise simplement les informations des dépôts configurés.

---

# ⬆️ Mettre à jour les paquets installés

Installer toutes les mises à jour disponibles :

```bash
sudo apt upgrade
```

ou :

```bash
sudo apt-get upgrade
```

Cette commande met à jour les logiciels déjà installés sans modifier la version de la distribution.

---

# 🔎 Rechercher un logiciel

Rechercher un paquet dans les dépôts :

```bash
sudo apt search <mot-clé>
```

Exemple :

```bash
sudo apt search nginx
```

La commande affiche les paquets correspondant au mot recherché.

---

# 📥 Installer un logiciel

Installer un paquet :

```bash
sudo apt install <nom_du_paquet>
```

Exemple :

```bash
sudo apt install htop
```

APT télécharge automatiquement le logiciel ainsi que ses dépendances.

---

# 🗑️ Supprimer complètement un paquet

Supprimer un paquet ainsi que ses fichiers de configuration :

```bash
sudo dpkg --purge <nom_du_paquet>
```

Exemple :

```bash
sudo dpkg --purge apache2
```

> [!TIP]  
> Une alternative couramment utilisée consiste à utiliser :

```bash
sudo apt purge <nom_du_paquet>
```

qui supprime également les fichiers de configuration du paquet.

---

# 🖥️ Afficher les informations système

Installer **Neofetch** :

```bash
sudo apt install neofetch
```

Puis l'exécuter :

```bash
neofetch
```

Neofetch affiche notamment :

- Distribution Linux.

- Version du noyau.

- Temps de fonctionnement.

- Environnement de bureau.

- CPU.

- RAM.

- Résolution d'écran.

> [!NOTE]  
> Neofetch n'est plus maintenu, mais reste largement utilisé. Son successeur est **Fastfetch**, plus rapide et activement développé.

---

# 🧰 Installer des utilitaires courants

Installer plusieurs outils utiles en une seule commande :

```bash
sudo apt install -y htop tree git curl unzip
```

Description des paquets :

| Paquet  | Description                                               |
| ------- | --------------------------------------------------------- |
| `htop`  | Moniteur interactif des processus système                 |
| `tree`  | Affiche l'arborescence des dossiers                       |
| `git`   | Gestionnaire de versions Git                              |
| `curl`  | Client HTTP pour télécharger ou interroger des ressources |
| `unzip` | Extraction des archives ZIP                               |

Le paramètre :

```text
-y
```

permet de répondre automatiquement **Oui** aux demandes de confirmation.

---

# 💡 Bonnes pratiques

- Toujours commencer par :

```bash
sudo apt update
```

avant une installation ou une mise à jour.

- Mettre régulièrement les paquets à jour avec :

```bash
sudo apt upgrade
```

- Installer uniquement les paquets provenant de dépôts de confiance.

- Utiliser `apt` pour les commandes interactives et réserver `apt-get` aux scripts ou à des besoins de compatibilité.

> [!TIP]  
> Pour nettoyer les dépendances devenues inutiles après des désinstallations :

```bash
sudo apt autoremove
```

Et pour vider le cache des paquets téléchargés :

```bash
sudo apt clean
```
