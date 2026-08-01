# Craquer des mots de passe avec John the Ripper

## 📖 Description

**John the Ripper** est un outil open source de récupération de mots de passe. Il est principalement utilisé lors d'audits de sécurité, de tests d'intrusion ou d'exercices de cybersécurité afin d'évaluer la robustesse des mots de passe.

Il permet notamment de :

- Craquer des hashs de mots de passe.

- Tester des attaques par dictionnaire.

- Effectuer des attaques par force brute.

- Récupérer les mots de passe de nombreuses archives protégées (ZIP, RAR, etc.).

> [!IMPORTANT]  
> John the Ripper doit être utilisé uniquement sur des systèmes ou des fichiers pour lesquels vous disposez d'une autorisation explicite. Toute utilisation sur des données appartenant à un tiers sans autorisation est illégale.

---

## 📋 Prérequis

- Distribution Linux (Kali Linux recommandée).

- Accès à un terminal.

- Droits suffisants pour installer les paquets.

---

# ⚙️ Installation

Installer John the Ripper :

```bash
sudo apt install john
```

Vérifier l'installation :

```bash
john --version
```

---

# 🔐 Craquer le mot de passe d'une archive ZIP

## 1. Extraire le hash

Se placer dans le dossier contenant l'archive :

```bash
cd /chemin/vers/le/dossier
```

Extraire le hash :

```bash
zip2john archive.zip > hash.txt
```

Cette commande extrait le hash de l'archive protégée et l'enregistre dans un fichier nommé `hash.txt`.

---

## 2. Lancer le craquage

```bash
john hash.txt
```

John tente automatiquement plusieurs méthodes de cassage de mot de passe.

---

# 📦 Craquer une archive RAR

Extraire le hash :

```bash
rar2john archive.rar > hash.txt
```

Puis lancer le craquage :

```bash
john hash.txt
```

---

# 📖 Utiliser un dictionnaire personnalisé

Il est possible d'utiliser une liste de mots de passe personnalisée :

```bash
john --wordlist=/home/kali/wordlistperso.txt hash.txt
```

Remplacer :

```text
/home/kali/wordlistperso.txt
```

par le chemin de votre dictionnaire.

Cette méthode est généralement beaucoup plus rapide qu'une attaque par force brute lorsque le mot de passe est présent dans la liste.

---

# 🔍 Afficher le mot de passe trouvé

Une fois le mot de passe découvert :

```bash
john --show hash.txt
```

Cette commande affiche le ou les mots de passe retrouvés.

---

# 🧹 Reprendre une session interrompue

John sauvegarde automatiquement sa progression.

Pour reprendre une attaque interrompue :

```bash
john --restore
```

---

# 💡 Bonnes pratiques

- Privilégier une attaque par dictionnaire avant une attaque par force brute.

- Utiliser des dictionnaires adaptés au contexte de l'audit.

- Conserver les fichiers de hash séparément des fichiers d'origine.

- Tester plusieurs dictionnaires avant de lancer une attaque exhaustive.

> [!TIP]  
> Kali Linux fournit déjà plusieurs dictionnaires dans :

```text
/usr/share/wordlists/
```

Le plus connu est **rockyou.txt**, souvent utilisé lors des tests de pénétration :

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
```

---

# 📚 Formats supportés

John the Ripper prend en charge de nombreux formats, notamment :

- ZIP

- RAR

- PDF

- Office (Word, Excel, PowerPoint)

- Hashs Windows (NTLM)

- Hashs Linux (`/etc/shadow`)

- SHA-1, SHA-256, SHA-512

- MD5

- Et de nombreux autres formats via les versions Jumbo.

---

# 🔗 Outils associés

Lors d'un audit de sécurité, John the Ripper est souvent utilisé avec :

- **Hashcat** pour le craquage accéléré par GPU.

- **Hydra** pour les attaques en ligne sur des services réseau.

- **CeWL** pour générer des dictionnaires personnalisés.

- **Crunch** pour créer des listes de mots de passe.
