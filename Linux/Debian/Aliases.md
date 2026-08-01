# Créer et gérer des alias dans le shell Linux

## 📖 Description

Les **alias** permettent de créer des raccourcis pour des commandes fréquemment utilisées.

Ils remplacent une commande ou une suite de commandes par un nom plus court, ce qui facilite l'utilisation quotidienne du terminal.

Exemple :

```bash
alias ll="ls -l"
```

Lorsque l'utilisateur exécute :

```bash
ll
```

Le shell exécute automatiquement :

```bash
ls -l
```

Les alias sont très utiles pour :

- Gagner du temps.

- Simplifier des commandes longues.

- Personnaliser son environnement de travail.

---

## 📋 Prérequis

- Un shell compatible (Bash, Zsh…).

- Aucune permission particulière n'est requise.

---

# ⚙️ Créer un alias

Syntaxe :

```bash
alias <nom_alias>="<commande>"
```

Exemple :

```bash
alias ll="ls -l"
```

Créer un alias pour afficher les fichiers cachés :

```bash
alias la="ls -la"
```

Créer un alias pour mettre à jour un système Debian/Ubuntu :

```bash
alias maj="sudo apt update && sudo apt upgrade"
```

---

# 📄 Lister les alias existants

Afficher tous les alias de la session en cours :

```bash
alias
```

Afficher un alias spécifique :

```bash
alias ll
```

Exemple de résultat :

```text
alias ll='ls -l'
```

---

# ❌ Supprimer un alias

Supprimer un alias :

```bash
unalias <nom_alias>
```

Exemple :

```bash
unalias ll
```

L'alias est supprimé de la session courante.

---

# 💾 Rendre un alias permanent

Par défaut, un alias est perdu à la fermeture du terminal.

Pour le conserver, ajouter la commande dans le fichier de configuration du shell.

Pour Bash :

```bash
nano ~/.bashrc
```

Ajouter par exemple :

```bash
alias ll="ls -l"
alias la="ls -la"
alias maj="sudo apt update && sudo apt upgrade"
```

Recharger la configuration sans fermer la session :

```bash
source ~/.bashrc
```

> [!NOTE]  
> Selon le shell utilisé, le fichier de configuration peut être différent (`~/.zshrc` pour Zsh, par exemple).

---

# 💡 Exemples d'alias utiles

Afficher les fichiers avec détails :

```bash
alias ll="ls -l"
```

Afficher tous les fichiers, y compris les fichiers cachés :

```bash
alias la="ls -la"
```

Revenir au dossier personnel :

```bash
alias home="cd ~"
```

Mettre à jour une distribution Debian/Ubuntu :

```bash
alias maj="sudo apt update && sudo apt upgrade"
```

---

# 🛠️ Bonnes pratiques

- Choisir des noms d'alias courts et explicites.

- Éviter de remplacer des commandes système importantes (`rm`, `cp`, `mv`, etc.) sauf si le comportement est parfaitement maîtrisé.

- Regrouper les alias personnels dans le fichier `~/.bashrc` ou `~/.zshrc`.

- Documenter les alias utilisés sur les serveurs afin de faciliter leur maintenance.

> [!TIP]  
> Après avoir modifié le fichier `~/.bashrc`, rechargez-le avec :

```bash
source ~/.bashrc
```

Les nouveaux alias seront immédiatement disponibles sans avoir à ouvrir un nouveau terminal.
