# Migration d'un serveur DHCP

## 📖 Description

Cette procédure permet d'exporter la configuration d'un serveur DHCP Windows, puis de l'importer sur un autre serveur. L'export comprend notamment les étendues (Scopes), réservations, options et baux DHCP.

> [!IMPORTANT]
> Exécuter les commandes dans une invite de commandes ou une console PowerShell **ouverte en tant qu'administrateur**.

---

## 📋 Prérequis

- Rôle **Serveur DHCP** installé sur le serveur de destination.
- Droits administrateur sur les deux serveurs.
- Le fichier d'export (`dhcp.txt`) doit être accessible sur le serveur de destination.

---

## ⚙️ Export de la configuration

Exécuter la commande suivante sur le serveur DHCP source :

```cmd
netsh dhcp server export C:\dhcp.txt
```

Cette commande exporte l'ensemble de la configuration DHCP dans le fichier `C:\dhcp.txt`.

---

## ⚙️ Import de la configuration

Copier le fichier `dhcp.txt` sur le nouveau serveur, puis exécuter :

```cmd
netsh dhcp server import C:\dhcp.txt
```

La configuration est alors importée sur le serveur DHCP de destination.

---

## ✅ Vérification

Après l'import, vérifier que :

- Les étendues DHCP sont présentes.
- Les réservations ont bien été importées.
- Les options DHCP sont correctement configurées.
- Le service DHCP est démarré.

---

> [!TIP]
> Avant de mettre le nouveau serveur en production, il est recommandé de désactiver ou d'arrêter le service DHCP sur l'ancien serveur afin d'éviter que deux serveurs DHCP distribuent des adresses sur le même réseau.
