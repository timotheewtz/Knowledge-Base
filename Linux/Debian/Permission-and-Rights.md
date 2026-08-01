# Gérer les permissions des fichiers et dossiers sous Linux

## 📖 Description

Sous Linux, chaque fichier et dossier possède des **permissions** qui déterminent les actions autorisées pour les différents utilisateurs.

Les permissions permettent notamment de :

- Contrôler qui peut lire un fichier.

- Autoriser ou non sa modification.

- Déterminer si un fichier peut être exécuté comme un programme ou un script.

La commande `chmod` permet de modifier rapidement ces permissions.

---

## 📋 Prérequis

- Accès à un terminal Linux.

- Être propriétaire du fichier ou disposer des privilèges `sudo`.

---

# 🔍 Afficher les permissions

Afficher les permissions d'un fichier ou d'un dossier :

```bash
ls -l
```

Exemple :

```text
-rwxr-xr-- 1 timothee users 2048 Jul 31 script.sh
```

Décomposition :

```text
-rwxr-xr--
```

| Élément | Description                           |
| ------- | ------------------------------------- |
| `-`     | Type de fichier (`d` pour un dossier) |
| `rwx`   | Permissions du propriétaire           |
| `r-x`   | Permissions du groupe                 |
| `r--`   | Permissions des autres utilisateurs   |

---

# 📖 Les permissions

Les trois permissions principales sont :

| Permission | Signification         |
| ---------- | --------------------- |
| `r`        | Lecture (*Read*)      |
| `w`        | Écriture (*Write*)    |
| `x`        | Exécution (*Execute*) |

Pour un dossier :

- `r` : permet de voir son contenu.

- `w` : permet d'ajouter, supprimer ou modifier des fichiers.

- `x` : permet d'entrer dans le dossier.

---

# ⚙️ Modifier les permissions avec chmod

## Ajouter une permission

Rendre un script exécutable :

```bash
chmod +x script.sh
```

Le script pourra ensuite être exécuté avec :

```bash
./script.sh
```

---

Retirer la permission d'exécution :

```bash
chmod -x script.sh
```

---

Ajouter la permission d'écriture :

```bash
chmod +w fichier.txt
```

---

Retirer la permission d'écriture :

```bash
chmod -w fichier.txt
```

---

# 🔢 Utiliser la notation numérique

Les permissions peuvent également être définies avec une valeur numérique.

| Valeur | Permissions |
| ------ | ----------- |
| 7      | rwx         |
| 6      | rw-         |
| 5      | r-x         |
| 4      | r--         |
| 0      | ---         |

Exemple :

```bash
chmod 755 script.sh
```

Correspond à :

```text
Propriétaire : rwx
Groupe       : r-x
Autres       : r-x
```

---

Quelques valeurs courantes :

| Valeur | Utilisation                                |
| ------ | ------------------------------------------ |
| 777    | Tous les droits pour tous (à éviter)       |
| 755    | Script ou dossier exécutable               |
| 750    | Exécutable réservé au groupe               |
| 644    | Fichier classique                          |
| 600    | Fichier privé (clés SSH, mots de passe...) |

---

# 👤 Modifier le propriétaire

Changer le propriétaire d'un fichier :

```bash
sudo chown utilisateur fichier.txt
```

Exemple :

```bash
sudo chown timothee script.sh
```

---

Changer le propriétaire et le groupe :

```bash
sudo chown utilisateur:groupe fichier.txt
```

Exemple :

```bash
sudo chown timothee:developers projet.sh
```

---

# 👥 Modifier le groupe

Changer uniquement le groupe :

```bash
sudo chgrp groupe fichier.txt
```

Exemple :

```bash
sudo chgrp developers script.sh
```

---

# 🔎 Vérifier le propriétaire

Afficher les permissions ainsi que le propriétaire :

```bash
ls -l
```

Afficher les informations détaillées :

```bash
stat fichier.txt
```

---

# 💡 Cas d'utilisation

## Rendre un script exécutable

```bash
chmod +x sauvegarde.sh
```

Puis :

```bash
./sauvegarde.sh
```

---

## Protéger une clé privée SSH

```bash
chmod 600 ~/.ssh/id_ed25519
```

---

## Donner les droits d'exécution sur un dossier

```bash
chmod 755 /opt/scripts
```

---

# 🛠️ Bonnes pratiques

- Attribuer uniquement les permissions nécessaires.

- Éviter autant que possible les permissions `777`.

- Utiliser `600` pour les fichiers sensibles (clés SSH, certificats, mots de passe).

- Vérifier les permissions avec `ls -l` après toute modification.

- Modifier le propriétaire avec `chown` plutôt que d'utiliser des permissions trop permissives.

> [!WARNING]  
> La commande :

```bash
chmod -R 777 /
```

est extrêmement dangereuse. Elle modifie récursivement les permissions de l'ensemble du système de fichiers et peut compromettre la sécurité ou le fonctionnement du système d'exploitation.

> [!TIP]  
> Pour modifier les permissions de manière récursive sur un dossier :

```bash
chmod -R 755 MonDossier
```

L'option `-R` applique les permissions à tous les sous-dossiers et fichiers contenus dans le répertoire.
