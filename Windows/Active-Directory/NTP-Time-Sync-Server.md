# Configurer un serveur NTP Windows

## 📖 Description

Le service **Windows Time (`w32time`)** permet à Windows de synchroniser son horloge avec une source de temps externe ou interne.

Dans un environnement **Active Directory**, le serveur **PDC Emulator** joue généralement le rôle de référence horaire pour le domaine.

Cette procédure permet de :

- Vérifier la source de temps actuelle.
- Comparer l'heure avec un serveur NTP externe.
- Configurer des serveurs NTP publics comme source de synchronisation.
- Déclarer le serveur Windows comme source de temps fiable pour le réseau.

> [!IMPORTANT]
> Une synchronisation horaire correcte est indispensable au bon fonctionnement d'Active Directory, notamment pour l'authentification Kerberos.

---

## 📋 Prérequis

- Serveur Windows avec droits administrateur.
- Accès Internet pour contacter les serveurs NTP publics (si utilisation d'une source externe).
- Port UDP 123 autorisé vers les serveurs NTP.
- Service Windows Time actif.

---

# 🔍 Vérifier la source de temps actuelle

Afficher la source NTP actuellement utilisée :

```cmd
w32tm /query /source
```

Exemple de résultat :

```text
VM IC Time Synchronization Provider
```

ou :

```text
NomDuServeurNTP
```

---

# 🔎 Comparer l'heure avec un serveur NTP externe

Effectuer une comparaison avec un serveur NTP public :

```cmd
w32tm /stripchart /computer:0.fr.pool.ntp.org
```

Cette commande affiche :

- La différence entre l'heure locale et le serveur NTP.
- Le décalage en millisecondes.
- La stabilité de la synchronisation.

---

# ⚙️ Configurer les serveurs NTP externes

Définir les serveurs NTP français du pool NTP :

```cmd
w32tm /config /manualpeerlist:"0.fr.pool.ntp.org,0x8 1.fr.pool.ntp.org,0x8 2.fr.pool.ntp.org,0x8" /syncfromflags:manual /update
```

Cette configuration utilise trois sources NTP publiques :

```text
0.fr.pool.ntp.org
1.fr.pool.ntp.org
2.fr.pool.ntp.org
```

Le paramètre :

```text
0x8
```

indique à Windows d'utiliser le mode client NTP.

---

# 🔄 Redémarrer le service Windows Time

Après modification de la configuration :

```cmd
net stop w32time
```

Puis :

```cmd
net start w32time
```

Forcer une synchronisation :

```cmd
w32tm /resync
```

---

# 🖥️ Déclarer le serveur comme source de temps fiable

Pour annoncer ce serveur comme référence horaire sur le réseau :

```cmd
w32tm /config /reliable:yes
```

Cette configuration est généralement appliquée sur :

- Le contrôleur de domaine ayant le rôle **PDC Emulator**.
- Un serveur NTP dédié.

---

# 🔍 Vérification

## Vérifier la configuration NTP

```cmd
w32tm /query /configuration
```

Permet de vérifier :

- La source NTP configurée.
- Le mode de synchronisation.
- Le statut de serveur fiable.

---

## Vérifier l'état de synchronisation

```cmd
w32tm /query /status
```

Informations affichées :

- Source utilisée.
- Dernière synchronisation.
- Nombre de tentatives.
- Précision de l'horloge.

---

## Vérifier la source actuelle

```cmd
w32tm /query /source
```

Résultat attendu :

```text
0.fr.pool.ntp.org
```

ou le serveur configuré.

---

# 💡 Bonnes pratiques

- Dans un domaine Active Directory, configurer uniquement le **PDC Emulator** avec une source NTP externe.
- Laisser les autres contrôleurs de domaine et postes clients suivre la hiérarchie AD.
- Éviter de configurer chaque machine du domaine avec des serveurs NTP publics.
- Toujours vérifier la synchronisation après modification.

> [!TIP]
> Pour identifier le serveur possédant le rôle PDC Emulator :

```cmd
netdom query fsmo
```

Le serveur indiqué comme **PDC** est généralement celui à configurer avec une source NTP externe.
