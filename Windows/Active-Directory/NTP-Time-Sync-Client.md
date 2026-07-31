# Réinitialiser et configurer la synchronisation NTP sur un poste client Windows

## 📖 Description

Windows utilise le service **Windows Time (`w32time`)** afin de synchroniser l'heure système avec une source de temps configurée.

Dans un environnement **Active Directory**, les postes clients synchronisent généralement leur horloge automatiquement depuis la hiérarchie du domaine, jusqu'au **PDC Emulator** du domaine.

Cette procédure permet de réinitialiser le service de temps Windows et de forcer une nouvelle synchronisation avec le domaine.

---

## 📋 Prérequis

- Poste Windows membre d'un domaine Active Directory.
- Compte administrateur local ou domaine.
- Connectivité réseau avec un contrôleur de domaine.
- DNS Active Directory fonctionnel.

> [!IMPORTANT]
> Une mauvaise synchronisation horaire peut provoquer des problèmes d'authentification Kerberos, notamment lors des connexions au domaine.

---

# ⚙️ Réinitialisation du service Windows Time

> [!WARNING]
> Exécuter les commandes suivantes **dans l'ordre indiqué** afin de correctement désinscrire puis réinscrire le service NTP Windows.

---

## 1. Arrêter le service Windows Time

```cmd
net stop w32time
```

Arrête le service responsable de la synchronisation horaire Windows.

---

## 2. Désinscrire le service NTP

```cmd
w32tm /unregister
```

Supprime l'enregistrement actuel du service Windows Time.

---

## 3. Réinscrire le service NTP

```cmd
w32tm /register
```

Réinscrit le service Windows Time dans le système.

---

## 4. Démarrer le service Windows Time

```cmd
net start w32time
```

Redémarre le service de synchronisation horaire.

---

# ⚙️ Forcer la synchronisation avec le domaine Active Directory

Configurer le poste pour utiliser la hiérarchie du domaine :

```cmd
w32tm /config /syncfromflags:DOMHIER /update
```

Cette commande indique à Windows d'utiliser la hiérarchie Active Directory comme source de temps.

---

## 🔄 Redémarrer le service après modification

Arrêter le service :

```cmd
net stop w32time
```

Puis le redémarrer :

```cmd
net start w32time
```

---

# 🔍 Vérification

## Afficher la source de temps actuelle

```cmd
w32tm /query /source
```

Résultat attendu dans un domaine :

```text
NomDuControleurDeDomaine
```

---

## Afficher l'état du service NTP

```cmd
w32tm /query /status
```

Permet de vérifier :

- La source de synchronisation.
- La dernière synchronisation réussie.
- La précision de l'horloge.

---

# 🖥️ Cas particulier : Machine virtuelle Hyper-V

Lorsqu'un poste Windows est virtualisé sous Hyper-V, il faut vérifier la configuration du service d'intégration :

```
Hyper-V Manager
→ Paramètres de la VM
→ Services d'intégration
→ Synchronisation date/heure
```

Désactiver :

```text
☐ Synchronisation date/heure
```

> [!IMPORTANT]
> Une VM membre d'un domaine Active Directory doit généralement utiliser la synchronisation NTP du domaine et non celle fournie par l'hyperviseur.

---

# 💡 Bonnes pratiques

- Toujours vérifier la source de temps avec :

```cmd
w32tm /query /source
```

- Dans un domaine Active Directory, le **PDC Emulator** doit être la référence horaire principale.
- Vérifier la configuration réseau et DNS avant de diagnostiquer un problème NTP.
