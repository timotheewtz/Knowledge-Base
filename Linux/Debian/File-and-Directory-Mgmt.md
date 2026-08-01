# Gestion des fichiers et dossiers sous Linux

## 📖 Description

Linux fournit de nombreuses commandes permettant de gérer les fichiers et dossiers directement depuis le terminal.

Ces commandes sont indispensables pour :

- Naviguer dans le système de fichiers.

- Créer, copier, déplacer ou supprimer des fichiers.

- Organiser des répertoires.

- Administrer un serveur Linux.

---

## 📋 Prérequis

- Accès à un terminal Linux.

- Les droits suffisants sur les fichiers ou dossiers concernés.

- Utiliser `sudo` lorsque des privilèges administrateur sont nécessaires.

---

# 📂 Afficher le contenu d'un dossier

Lister les fichiers et dossiers du répertoire courant :

```bash
ls
```

Afficher les détails :

```bash
ls -l
```

Afficher également les fichiers cachés :

```bash
ls -la
```

---

# 📍 Se déplacer dans les dossiers

Accéder à un dossier :

```bash
cd <chemin>
```

Exemple :

```bash
cd /var/log
```

Revenir au dossier précédent :

```bash
cd ..
```

Retourner dans son dossier personnel :

```bash
cd ~
```

Afficher le répertoire courant :

```bash
pwd
```

---

# 📁 Créer un dossier

Créer un dossier :

```bash
mkdir <nom_dossier>
```

Exemple :

```bash
mkdir Sauvegardes
```

Créer plusieurs niveaux de dossiers en une seule commande :

```bash
mkdir -p Projets/Linux/Scripts
```

---

# 📄 Créer un fichier

Créer un fichier vide :

```bash
touch fichier.txt
```

Créer plusieurs fichiers :

```bash
touch fichier1.txt fichier2.txt fichier3.txt
```

---

# 📋 Copier des fichiers ou dossiers

Copier un fichier :

```bash
cp fichier.txt sauvegarde.txt
```

Copier un dossier et son contenu :

```bash
cp -r Dossier Sauvegarde
```

---

# 📦 Déplacer ou renommer

Déplacer un fichier :

```bash
mv fichier.txt /home/user/Documents/
```

Renommer un fichier :

```bash
mv ancien.txt nouveau.txt
```

Renommer un dossier :

```bash
mv AncienDossier NouveauDossier
```

---

# 🗑️ Supprimer

Supprimer un fichier :

```bash
rm fichier.txt
```

Supprimer un dossier vide :

```bash
rmdir Dossier
```

Supprimer un dossier et tout son contenu :

```bash
rm -r Dossier
```

Forcer la suppression sans confirmation :

```bash
rm -rf Dossier
```

> [!WARNING]  
> La commande :

```bash
rm -rf
```

> supprime définitivement les fichiers sans passer par une corbeille. Une mauvaise utilisation peut entraîner une perte irréversible de données.

---

# 🔎 Rechercher un fichier

Rechercher un fichier dans le système :

```bash
find / -name "fichier.txt"
```

Rechercher dans un dossier spécifique :

```bash
find /home -name "*.log"
```

---

# 👀 Afficher le contenu d'un fichier

Afficher tout le contenu :

```bash
cat fichier.txt
```

Lire un fichier page par page :

```bash
less fichier.txt
```

Afficher les premières lignes :

```bash
head fichier.txt
```

Afficher les dernières lignes :

```bash
tail fichier.txt
```

Suivre un fichier de log en temps réel :

```bash
tail -f /var/log/syslog
```

---

# 📊 Afficher la taille des dossiers

Afficher la taille d'un dossier :

```bash
du -sh Dossier
```

Afficher l'espace disque disponible :

```bash
df -h
```

---

# 💡 Bonnes pratiques

- Vérifier le contenu d'un dossier avec `ls` avant de supprimer des fichiers.

- Utiliser `rm -rf` uniquement lorsque cela est nécessaire.

- Préférer `cp` avant `mv` lors d'opérations sensibles afin de conserver une copie.

- Utiliser des chemins absolus pour les scripts afin d'éviter les erreurs.

- Contrôler régulièrement l'espace disque avec `df -h` et `du -sh`.

> [!TIP]  
> Pour visualiser rapidement l'arborescence d'un dossier, installer l'utilitaire **tree** :

```bash
sudo apt install tree
```

Puis exécuter :

```bash
tree
```

ou pour un dossier spécifique :

```bash
tree /var/www
```
