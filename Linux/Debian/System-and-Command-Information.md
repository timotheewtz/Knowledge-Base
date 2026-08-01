# Obtenir des informations sur le système et les commandes Linux

## 📖 Description

Linux met à disposition de nombreuses commandes permettant d'obtenir rapidement des informations sur :

- L'utilisateur actuellement connecté.

- Le système d'exploitation.

- Le noyau Linux.

- Les commandes disponibles.

- Les informations matérielles.

Ces commandes sont particulièrement utiles lors du dépannage, de l'administration système ou de l'inventaire d'une machine.

---

## 📋 Prérequis

- Accès à un terminal Linux.

- Certaines commandes peuvent nécessiter l'installation d'un paquet supplémentaire.

---

# 👤 Afficher l'utilisateur connecté

Afficher le nom de l'utilisateur courant :

```bash
whoami
```

Cette commande retourne le nom du compte actuellement utilisé.

Exemple :

```text
timothee
```

Commande équivalente :

```bash
echo $USER
```

---

# 📖 Obtenir une description d'une commande

Afficher une description courte d'une commande :

```bash
whatis less
```

Exemple de résultat :

```text
less - opposite of more
```

> [!TIP]  
> Si aucune description n'est retournée, mettre à jour la base de données des pages de manuel :

```bash
sudo mandb
```

---

# 🖥️ Afficher les informations du système

Afficher le type de système :

```bash
uname
```

Afficher toutes les informations disponibles :

```bash
uname -a
```

Cette commande affiche notamment :

- Le nom du noyau.

- Le nom de la machine.

- La version du noyau.

- L'architecture (x86_64, ARM...).

- La date de compilation du noyau.

---

# 🎨 Afficher les informations système avec Fastfetch / Neofetch

## Fastfetch (recommandé)

Installer Fastfetch :

```bash
sudo apt install fastfetch
```

Lancer Fastfetch :

```bash
fastfetch
```

Fastfetch affiche notamment :

- Distribution Linux.

- Version du noyau.

- Temps de fonctionnement.

- CPU.

- GPU.

- Mémoire RAM.

- Résolution.

- Shell utilisé.

> [!NOTE]  
> **Fastfetch** est le successeur moderne de **Neofetch**. Il est plus rapide et est activement maintenu.

---

## Neofetch

Installer Neofetch :

```bash
sudo apt install neofetch
```

Lancer l'outil :

```bash
neofetch
```

Neofetch fournit également un résumé graphique des principales informations système.

---

# 🏷️ Afficher le nom de la machine

Afficher le nom d'hôte (*hostname*) :

```bash
hostname
```

Exemple :

```text
srv-web-01
```

Cette commande est très utilisée lors de connexions SSH.

---

# 🧠 Afficher l'architecture du système

Afficher uniquement l'architecture :

```bash
uname -m
```

Exemple :

```text
x86_64
```

ou

```text
aarch64
```

Cette information est utile pour télécharger la bonne version d'un logiciel.

---

# 📄 Consulter la version de la distribution

Afficher les informations de la distribution :

```bash
cat /etc/os-release
```

Exemple :

```text
PRETTY_NAME="Debian GNU/Linux 13 (trixie)"
```

Cette commande est très utilisée dans les scripts d'installation.

---

# 📚 Consulter le manuel d'une commande

Afficher la documentation complète :

```bash
man <commande>
```

Exemple :

```bash
man tar
```

Navigation :

- Flèches : déplacer la vue.

- `/` : rechercher un mot.

- `q` : quitter.

---

# 💡 Bonnes pratiques

- Utiliser `whoami` pour vérifier rapidement le compte actuellement utilisé.

- Utiliser `uname -a` lors d'un dépannage afin de connaître le noyau et l'architecture.

- Préférer **Fastfetch** à **Neofetch** sur les nouvelles distributions.

- Utiliser `man` pour découvrir toutes les options d'une commande.

- Utiliser `whatis` pour obtenir rapidement le rôle d'une commande sans ouvrir son manuel.

## 📚 Résumé des commandes

| Commande              | Description                                       |
| --------------------- | ------------------------------------------------- |
| `whoami`              | Affiche l'utilisateur connecté                    |
| `echo $USER`          | Affiche également l'utilisateur courant           |
| `whatis`              | Description rapide d'une commande                 |
| `man`                 | Documentation complète d'une commande             |
| `uname -a`            | Informations sur le noyau et le système           |
| `uname -m`            | Architecture du système                           |
| `hostname`            | Nom de la machine                                 |
| `cat /etc/os-release` | Version de la distribution Linux                  |
| `fastfetch`           | Résumé graphique des informations système         |
| `neofetch`            | Ancien outil d'affichage des informations système |
