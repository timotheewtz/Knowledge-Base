# Arrêter et redémarrer un système Linux

## 📖 Description

La commande `shutdown` permet de planifier l'arrêt ou le redémarrage d'un système Linux de manière contrôlée.

Contrairement à une extinction brutale, elle avertit les utilisateurs connectés, termine proprement les processus en cours et démonte les systèmes de fichiers avant l'arrêt de la machine.

Elle est couramment utilisée lors des opérations de maintenance, des mises à jour système ou des redémarrages planifiés.

---

## 📋 Prérequis

- Accès à un compte disposant des droits `sudo`.

- Les utilisateurs connectés doivent être informés si la machine est utilisée en production.

---

# 🛑 Arrêter immédiatement le système

Pour arrêter immédiatement la machine :

```bash
sudo shutdown now
```

Cette commande lance immédiatement la procédure d'arrêt du système.

---

# ⏳ Planifier un arrêt

Planifier un arrêt à une heure précise (format 24 heures) :

```bash
sudo shutdown 20:40
```

La machine s'éteindra automatiquement à **20h40**.

---

Planifier un arrêt dans un certain nombre de minutes :

```bash
sudo shutdown +30
```

La machine sera arrêtée dans **30 minutes**.

---

# ❌ Annuler un arrêt planifié

Si un arrêt a été lancé par erreur, il est possible de l'annuler :

```bash
sudo shutdown -c
```

Tous les utilisateurs connectés seront informés de l'annulation.

---

# 🔄 Redémarrer immédiatement

Pour redémarrer immédiatement le système :

```bash
sudo shutdown -r now
```

Le paramètre :

```text
-r
```

indique que la machine doit être **redémarrée** au lieu d'être arrêtée.

---

# ⏳ Planifier un redémarrage

Redémarrer dans 15 minutes :

```bash
sudo shutdown -r +15
```

Redémarrer à une heure précise :

```bash
sudo shutdown -r 23:00
```

---

# 📢 Envoyer un message aux utilisateurs

Il est possible d'afficher un message avant l'arrêt :

```bash
sudo shutdown +10 "Maintenance du serveur dans 10 minutes."
```

Les utilisateurs connectés recevront une notification avant l'arrêt.

---

# 🔎 Alternatives courantes

Arrêter immédiatement :

```bash
sudo poweroff
```

ou

```bash
sudo systemctl poweroff
```

---

Redémarrer immédiatement :

```bash
sudo reboot
```

ou

```bash
sudo systemctl reboot
```

Ces commandes sont aujourd'hui largement utilisées sur les distributions modernes utilisant **systemd**.

---

# 💡 Bonnes pratiques

- Prévenir les utilisateurs avant un arrêt planifié d'un serveur.

- Vérifier qu'aucune opération critique (sauvegarde, mise à jour, transfert de fichiers...) n'est en cours avant l'arrêt.

- Utiliser `shutdown` plutôt que d'éteindre brutalement la machine afin de garantir une fermeture propre des services et des systèmes de fichiers.

- Annuler immédiatement un arrêt accidentel avec `shutdown -c`.

> [!TIP]  
> Pour les serveurs administrés à distance, privilégier `shutdown` plutôt que `poweroff` ou `reboot`. Il permet de planifier un arrêt, d'envoyer un message aux utilisateurs et d'annuler facilement l'opération si nécessaire.
