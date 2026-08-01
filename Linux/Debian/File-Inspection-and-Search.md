# Consulter et rechercher dans des fichiers sous Linux

## 📖 Description

Linux propose de nombreuses commandes permettant d'afficher, parcourir, rechercher ou supprimer de manière sécurisée le contenu de fichiers.

Ces outils sont utilisés quotidiennement par les administrateurs système pour :

- Lire un fichier rapidement.

- Parcourir des fichiers volumineux.

- Consulter des journaux (*logs*).

- Rechercher un mot ou une expression.

- Localiser un programme.

- Supprimer définitivement des données sensibles.

---

## 📋 Prérequis

- Accès à un terminal Linux.

- Les droits de lecture sur les fichiers concernés.

- Les droits d'écriture pour les opérations de suppression.

---

# 📄 Afficher un fichier avec `cat`

La commande `cat` (*concatenate*) permet principalement d'afficher le contenu d'un fichier directement dans le terminal.

```bash
cat fichier.txt
```

Concaténer plusieurs fichiers :

```bash
cat fichier1.txt fichier2.txt
```

Créer rapidement un fichier :

```bash
cat > fichier.txt
```

Terminer la saisie avec :

```text
CTRL + D
```

> [!TIP]  
> `cat` est idéal pour les petits fichiers. Pour les fichiers volumineux, privilégier `less`.

---

# 📖 Parcourir un fichier avec `less`

Afficher un fichier dans une interface interactive :

```bash
less fichier.txt
```

Fonctionnalités utiles :

- Navigation avec les flèches.

- Recherche avec `/`.

- Aller à la fin avec `G`.

- Aller au début avec `g`.

- Quitter avec `q`.

Contrairement à `cat`, le contenu n'est pas entièrement affiché d'un seul coup.

---

# 🔝 Afficher les premières lignes

Afficher les 10 premières lignes :

```bash
head fichier.txt
```

Afficher un nombre précis de lignes :

```bash
head -n 20 fichier.txt
```

---

# 🔚 Afficher les dernières lignes

Afficher les 10 dernières lignes :

```bash
tail fichier.txt
```

Afficher les 30 dernières lignes :

```bash
tail -n 30 fichier.txt
```

Suivre un fichier de log en temps réel :

```bash
tail -f /var/log/syslog
```

Cette commande est très utilisée pour surveiller les journaux système.

---

# 🔎 Rechercher dans un fichier avec `grep`

Rechercher un mot :

```bash
grep "erreur" fichier.txt
```

Compter le nombre d'occurrences :

```bash
grep -c "erreur" fichier.txt
```

Recherche insensible à la casse :

```bash
grep -i "nginx" fichier.txt
```

Rechercher dans plusieurs fichiers :

```bash
grep "root" *.txt
```

> [!TIP]  
> `grep` est très souvent combiné avec d'autres commandes grâce aux pipes (`|`).

Exemple :

```bash
ps aux | grep apache
```

---

# 📍 Localiser un programme

Afficher le chemin d'une commande :

```bash
which bash
```

Exemple :

```bash
which git
```

Résultat :

```text
/usr/bin/git
```

Cette commande permet de vérifier où est installé un programme.

---

# 🛡️ Supprimer définitivement un fichier

La commande `shred` réécrit plusieurs fois le contenu d'un fichier afin de rendre sa récupération beaucoup plus difficile.

Réécrire le fichier :

```bash
shred fichier.txt
```

Réécrire puis supprimer le fichier :

```bash
shred -u fichier.txt
```

> [!IMPORTANT]  
> Contrairement à `rm`, `shred` tente d'empêcher la récupération des données en écrivant plusieurs fois sur le fichier avant sa suppression.

> [!NOTE]  
> Sur les SSD modernes ou les systèmes de fichiers avec journalisation ou mécanismes de copie (Copy-on-Write), `shred` ne garantit pas toujours une suppression totalement irréversible. Il reste néanmoins utile sur de nombreux supports de stockage classiques.

---

# 🔢 Compter les lignes, mots et caractères

La commande `wc` (*Word Count*) permet d'obtenir des statistiques sur le contenu d'un fichier.

Par défaut, elle affiche :

- Le nombre de lignes.

- Le nombre de mots.

- Le nombre de caractères (ou d'octets selon les options).

- Le nom du fichier.

Exemple :

```bash
wc fichier.txt
```

Résultat :

```text
25 180 1324 fichier.txt
```

Où :

- `25` correspond au nombre de lignes.

- `180` correspond au nombre de mots.

- `1324` correspond au nombre de caractères.



## 📋 Options courantes

Afficher uniquement le nombre de mots :

```bash
wc -w fichier.txt
```

Afficher uniquement le nombre de lignes :

```bash
wc -l fichier.txt
```

Afficher uniquement le nombre de caractères :

```bash
wc -m fichier.txt
```

Afficher uniquement la taille en octets :

```bash
wc -c fichier.txt
```

> [!TIP]  
> La commande `wc` est souvent combinée avec un pipe (`|`) afin de compter le nombre de résultats retournés par une autre commande.

Exemple :

```bash
ps aux | wc -l
```

Cette commande affiche le nombre total de processus actuellement en cours d'exécution.

---

# 💡 Bonnes pratiques

- Utiliser `cat` uniquement pour les petits fichiers.

- Préférer `less` pour parcourir des fichiers volumineux.

- Utiliser `tail -f` pour surveiller les journaux en temps réel.

- Combiner `grep` avec d'autres commandes pour filtrer les résultats.

- Vérifier le chemin d'un programme avec `which` avant de modifier une configuration.

- Réserver `shred` aux fichiers contenant des informations sensibles.

## 📚 Résumé des commandes

| Commande  | Utilisation                                             |
| --------- | ------------------------------------------------------- |
| `cat`     | Afficher ou concaténer des fichiers                     |
| `less`    | Parcourir un fichier de manière interactive             |
| `head`    | Afficher les premières lignes                           |
| `tail`    | Afficher les dernières lignes                           |
| `tail -f` | Suivre un fichier en temps réel                         |
| `grep`    | Rechercher du texte dans un ou plusieurs fichiers       |
| `which`   | Afficher le chemin d'un programme                       |
| `shred`   | Réécrire puis supprimer un fichier de manière sécurisée |
