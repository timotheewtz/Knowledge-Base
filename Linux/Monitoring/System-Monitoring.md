# Surveiller les ressources système sous Linux

## 📖 Description

Linux propose plusieurs outils permettant de surveiller l'état du système en temps réel.

Ces commandes permettent notamment de consulter :

- L'utilisation du processeur (CPU).

- La consommation de mémoire (RAM).

- Les processus en cours d'exécution.

- L'espace disque.

- La charge du système.

- Le temps de fonctionnement (*uptime*).

L'outil le plus populaire est **htop**, souvent considéré comme l'équivalent du **Gestionnaire des tâches** sous Windows.

---

## 📋 Prérequis

- Accès à un terminal Linux.

- Droits `sudo` pour installer certains outils.

---

# 📊 htop

## Installation

Installer **htop** :

```bash
sudo apt install htop
```

---

## Utilisation

Lancer l'interface :

```bash
htop
```

L'application affiche en temps réel :

- L'utilisation du CPU.

- La consommation de RAM et de Swap.

- Les processus actifs.

- La charge système.

- Le temps de fonctionnement du serveur.

Depuis l'interface, il est notamment possible de :

- Rechercher un processus.

- Trier par utilisation CPU ou mémoire.

- Terminer un processus (`F9`).

- Changer le mode d'affichage.

> [!TIP]  
> Utiliser les flèches du clavier pour naviguer dans les processus et les touches de fonction (`F1` à `F10`) pour accéder aux différentes actions.

---

# 📈 top

La plupart des distributions Linux disposent déjà de l'outil **top**.

```bash
top
```

Il fournit les mêmes informations principales que `htop`, mais avec une interface plus simple et moins interactive.

Quitter avec :

```text
q
```

---

# 🧠 Consommation mémoire

Afficher la mémoire utilisée :

```bash
free -h
```

L'option `-h` affiche les valeurs dans un format lisible (Mo, Go...).

---

# 💾 Utilisation des disques

Afficher l'espace disque disponible :

```bash
df -h
```

Afficher la taille d'un dossier :

```bash
du -sh <dossier>
```

Exemple :

```bash
du -sh /var/log
```

---

# ⚙️ Charge du système

Afficher le temps de fonctionnement ainsi que la charge moyenne :

```bash
uptime
```

Cette commande indique notamment :

- Depuis combien de temps la machine est allumée.

- Le nombre d'utilisateurs connectés.

- La charge système sur 1, 5 et 15 minutes.

---

# 🔎 Afficher les processus

Lister les processus actifs :

```bash
ps aux
```

Rechercher un processus spécifique :

```bash
ps aux | grep nginx
```

---

# 🛠️ Terminer un processus

Terminer un processus à partir de son PID :

```bash
kill <PID>
```

Forcer son arrêt :

```bash
kill -9 <PID>
```

Exemple :

```bash
kill -9 1524
```

> [!WARNING]  
> `kill -9` force immédiatement l'arrêt du processus sans lui laisser le temps de se fermer proprement. À utiliser uniquement lorsque cela est nécessaire.

---

# 💡 Bonnes pratiques

- Installer **htop** sur tous les serveurs administrés régulièrement.

- Utiliser `top` lorsque `htop` n'est pas disponible.

- Vérifier régulièrement la mémoire (`free -h`) et l'espace disque (`df -h`).

- Préférer un arrêt propre d'un service (`systemctl stop`) avant d'utiliser `kill -9`.

- Identifier la cause d'une consommation anormale avant de terminer un processus.

> [!TIP]  
> Si **htop** n'est plus maintenu sur certaines distributions ou si tu recherches davantage de fonctionnalités, tu peux installer **btop**, une alternative moderne offrant une interface plus riche et un suivi du CPU, de la mémoire, du disque et du réseau.

```bash
sudo apt install btop
```

Puis l'exécuter :

```bash
btop
```
