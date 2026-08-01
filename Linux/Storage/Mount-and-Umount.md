# Monter et démonter des systèmes de fichiers sous Linux

## 📖 Description

Sous Linux, les périphériques de stockage (disques, partitions, clés USB, partages réseau...) doivent être **montés** afin de devenir accessibles dans l'arborescence du système.

Contrairement à Windows où chaque disque possède une lettre (`C:`, `D:`...), Linux attache les systèmes de fichiers à un **point de montage** (*mount point*), qui est simplement un dossier.

Les commandes `mount` et `umount` permettent respectivement de monter et démonter ces systèmes de fichiers.

---

## 📋 Prérequis

- Accès à un terminal Linux.

- Les privilèges `sudo` sont généralement nécessaires.

- Un point de montage existant (répertoire vide).

---

# 💽 Lister les systèmes de fichiers montés

Afficher tous les systèmes de fichiers actuellement montés :

```bash
mount
```

Ou de manière plus lisible :

```bash
findmnt
```

---

# 💾 Identifier les disques

Lister les disques et partitions :

```bash
lsblk
```

Exemple :

```text
NAME   SIZE TYPE MOUNTPOINT
sda    500G disk
├─sda1 512M part /boot
└─sda2 499G part /
sdb      1T disk
└─sdb1   1T part
```

Pour afficher également les UUID et le type de système de fichiers :

```bash
lsblk -f
```

---

# 📁 Créer un point de montage

Créer un dossier qui servira de point de montage :

```bash
sudo mkdir /mnt/disque
```

Il est courant d'utiliser :

- `/mnt`

- `/media`

pour monter temporairement des périphériques.

---

# 📂 Monter un système de fichiers

Monter une partition :

```bash
sudo mount /dev/sdb1 /mnt/disque
```

Le contenu du disque sera alors accessible depuis :

```text
/mnt/disque
```

---

# 📀 Monter une clé USB

Après avoir identifié son nom avec `lsblk` :

```bash
sudo mount /dev/sdb1 /mnt/usb
```

---

# 📀 Démonter un système de fichiers

Démonter une partition :

```bash
sudo umount /mnt/disque
```

Ou directement avec le périphérique :

```bash
sudo umount /dev/sdb1
```

> [!IMPORTANT]  
> Il est recommandé de toujours démonter correctement un périphérique avant de le débrancher afin d'éviter toute corruption de données.

---

# ⚠️ Démonter un périphérique occupé

Si le message :

```text
target is busy
```

apparaît, cela signifie qu'un programme utilise encore le point de montage.

Identifier les processus concernés :

```bash
sudo lsof /mnt/disque
```

ou

```bash
sudo fuser -vm /mnt/disque
```

---

# 📄 Consulter le fichier fstab

Afficher la configuration des montages automatiques :

```bash
cat /etc/fstab
```

Ce fichier permet de définir les systèmes de fichiers montés automatiquement au démarrage.

---

# 🔄 Tester le fichier fstab

Après une modification de `/etc/fstab`, tester la configuration sans redémarrer :

```bash
sudo mount -a
```

Si aucune erreur n'est affichée, la configuration est généralement correcte.

---

# 🧾 Identifier les UUID

Afficher les UUID des partitions :

```bash
sudo blkid
```

Les UUID sont recommandés dans `/etc/fstab`, car ils restent identiques même si le nom du périphérique (`/dev/sdb`, `/dev/sdc`...) change.

---

# 💡 Bonnes pratiques

- Utiliser `lsblk` avant toute opération sur un disque.

- Préférer les **UUID** aux noms de périphériques dans `/etc/fstab`.

- Toujours démonter une clé USB ou un disque externe avant de le retirer.

- Tester les modifications du fichier `/etc/fstab` avec `mount -a` avant de redémarrer.

- Vérifier le contenu d'un point de montage avec `findmnt` ou `mount`.

## 📚 Résumé des commandes

| Commande                  | Description                                            |
| ------------------------- | ------------------------------------------------------ |
| `lsblk`                   | Afficher les disques et partitions                     |
| `lsblk -f`                | Afficher les systèmes de fichiers et UUID              |
| `mount`                   | Lister les systèmes de fichiers montés                 |
| `mount /dev/sdX /mnt/...` | Monter un système de fichiers                          |
| `umount /mnt/...`         | Démonter un système de fichiers                        |
| `findmnt`                 | Afficher les points de montage                         |
| `blkid`                   | Afficher les UUID des partitions                       |
| `cat /etc/fstab`          | Afficher les montages automatiques                     |
| `mount -a`                | Tester le fichier `/etc/fstab`                         |
| `lsof`                    | Identifier les processus utilisant un point de montage |
| `fuser`                   | Afficher les processus bloquant un démontage           |

> [!TIP]  
> Les commandes `lsblk`, `mount`, `findmnt`, `blkid` et `cat /etc/fstab` font partie des premières commandes qu'un administrateur système utilise lorsqu'il doit diagnostiquer un problème de disque ou monter un nouveau périphérique.
