# Configurer le fuseau horaire et les locales sous Linux

## 📖 Description

Sous Linux, la date, l'heure et les paramètres régionaux (**locales**) sont essentiels au bon fonctionnement du système.

Ils permettent notamment de définir :

- Le fuseau horaire.

- Le format de la date et de l'heure.

- La langue du système.

- Le format des nombres et devises.

Cette procédure s'applique principalement aux distributions **Debian** et **Ubuntu**.

---

## 📋 Prérequis

- Compte disposant des droits `sudo`.

- Distribution Linux basée sur Debian.

- Service `systemd` installé (pour `timedatectl`).

---

# 🌍 Configurer le fuseau horaire

Définir le fuseau horaire sur **Europe/Paris** :

```bash
sudo timedatectl set-timezone Europe/Paris
```

Cette commande modifie immédiatement le fuseau horaire du système.

---

## 🔍 Vérifier la configuration

Afficher la configuration actuelle de la date, de l'heure et du fuseau horaire :

```bash
timedatectl
```

Exemple de résultat :

```text
Local time: Mon 2026-08-03 10:15:42 CEST
Universal time: Mon 2026-08-03 08:15:42 UTC
RTC time: Mon 2026-08-03 08:15:41
Time zone: Europe/Paris (CEST, +0200)
System clock synchronized: yes
NTP service: active
```

---

# 🌐 Configurer les locales

Lancer l'assistant de configuration des locales :

```bash
sudo dpkg-reconfigure locales
```

Cet assistant permet notamment de :

- Choisir la langue du système.

- Générer les locales souhaitées.

- Définir la locale par défaut.

Par exemple :

```text
fr_FR.UTF-8
```

ou

```text
en_US.UTF-8
```

---

## 🔎 Vérifier les locales configurées

Afficher la locale actuellement utilisée :

```bash
locale
```

Afficher toutes les locales disponibles :

```bash
locale -a
```

---

## 💡 Bonnes pratiques

- Utiliser un fuseau horaire correspondant à l'emplacement du serveur ou de l'utilisateur.

- Privilégier les locales **UTF-8** pour garantir une bonne gestion des caractères spéciaux.

- Vérifier la configuration après une installation ou une migration de serveur.

- Synchroniser l'heure avec un serveur NTP pour assurer une horloge précise.

> [!TIP]  
> Pour afficher la liste des fuseaux horaires disponibles :

```bash
timedatectl list-timezones
```

Il est possible de rechercher un fuseau spécifique :

```bash
timedatectl list-timezones | grep Europe
```
