# Gérer les archives et la compression sous Linux

## 📖 Description

Linux propose plusieurs outils permettant de créer, compresser et extraire des archives.

Les plus utilisés sont :

- **tar** : créer et extraire des archives.

- **gzip** : compresser une archive au format `.gz`.

- **bzip2** : compression plus efficace mais plus lente.

- **xz** : très forte compression.

- **zip / unzip** : compatible avec Windows et la plupart des systèmes d'exploitation.

---

## 📋 Prérequis

- Accès à un terminal Linux.

- Installer le paquet `unzip` si nécessaire :

```bash
sudo apt install unzip
```

Pour créer des archives ZIP :

```bash
sudo apt install zip
```

---

# 📦 Décompresser une archive ZIP

Extraire une archive dans le dossier courant :

```bash
unzip archive.zip
```

Extraire dans un dossier spécifique :

```bash
unzip archive.zip -d /chemin/vers/le/dossier
```

---

# 📦 Créer une archive ZIP

Compresser un fichier :

```bash
zip archive.zip fichier.txt
```

Compresser plusieurs fichiers :

```bash
zip archive.zip fichier1.txt fichier2.txt
```

Compresser un dossier et tout son contenu :

```bash
zip -r archive.zip MonDossier
```

L'option `-r` signifie **récursif**.

---

# 📁 Créer une archive TAR

Créer une archive sans compression :

```bash
tar -cvf archive.tar MonDossier/
```

### Explication des options

| Option | Description                               |
| ------ | ----------------------------------------- |
| `c`    | Créer une archive                         |
| `v`    | Afficher les fichiers traités (*Verbose*) |
| `f`    | Nom du fichier archive                    |

---

# 📂 Extraire une archive TAR

```bash
tar -xvf archive.tar
```

### Explication des options

| Option | Description                    |
| ------ | ------------------------------ |
| `x`    | Extraire l'archive             |
| `v`    | Afficher les fichiers extraits |
| `f`    | Nom de l'archive               |

---

# 📦 Créer une archive TAR.GZ

Le format **tar.gz** est le plus utilisé sous Linux.

Créer une archive compressée :

```bash
tar -czvf archive.tar.gz MonDossier/
```

Le paramètre :

```text
z
```

indique que la compression est réalisée avec **gzip**.

---

# 📂 Extraire une archive TAR.GZ

```bash
tar -xzvf archive.tar.gz
```

---

# 📦 Créer une archive TAR.XZ

Le format `.tar.xz` offre un meilleur taux de compression.

Créer l'archive :

```bash
tar -cJvf archive.tar.xz MonDossier/
```

---

# 📂 Extraire une archive TAR.XZ

```bash
tar -xJvf archive.tar.xz
```

---

# 📦 Créer une archive TAR.BZ2

Créer une archive compressée avec **bzip2** :

```bash
tar -cjvf archive.tar.bz2 MonDossier/
```

---

# 📂 Extraire une archive TAR.BZ2

```bash
tar -xjvf archive.tar.bz2
```

---

# 🔎 Afficher le contenu d'une archive TAR

Lister les fichiers contenus dans une archive sans l'extraire :

```bash
tar -tvf archive.tar
```

---

# 💡 Formats les plus courants

| Extension  | Description                                   |
| ---------- | --------------------------------------------- |
| `.zip`     | Compatible Windows, Linux et macOS            |
| `.tar`     | Archive sans compression                      |
| `.tar.gz`  | Archive compressée avec Gzip (très courant)   |
| `.tar.bz2` | Compression Bzip2                             |
| `.tar.xz`  | Compression XZ (meilleur taux de compression) |

---

# 🛠️ Bonnes pratiques

- Utiliser **ZIP** pour partager des fichiers avec des utilisateurs Windows.

- Privilégier **tar.gz** pour les sauvegardes et les transferts sous Linux.

- Utiliser **tar.xz** lorsque la taille de l'archive est prioritaire.

- Vérifier le contenu d'une archive avec `tar -tvf` avant de l'extraire.

- Conserver l'arborescence d'origine lors de la création d'archives afin de faciliter leur restauration.

> [!TIP]  
> Si tu oublies les options de `tar`, retiens simplement les deux commandes les plus utilisées :

Créer une archive compressée :

```bash
tar -czvf archive.tar.gz MonDossier/
```

Extraire une archive compressée :

```bash
tar -xzvf archive.tar.gz
```

Ces deux commandes couvrent la majorité des cas rencontrés en administration système Linux.
