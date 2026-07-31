# Vérifier l'appartenance à un domaine Active Directory

## 📖 Description

Cette commande permet de vérifier rapidement si un poste Windows est rattaché à un **domaine Active Directory** et d'afficher le nom du domaine associé.

Elle est utile lors de :

- Diagnostics de poste utilisateur.
- Vérification avant une migration de domaine.
- Dépannage d'authentification Active Directory.
- Contrôle rapide de la configuration d'un poste.

---

## ⚙️ Vérifier le domaine du poste

Exécuter la commande suivante dans PowerShell :

```powershell
(Get-WmiObject Win32_ComputerSystem).Domain
```

---

## 🔍 Résultat

### Poste membre d'un domaine

Exemple :

```text
entreprise.local
```

Le poste est joint au domaine Active Directory indiqué.

---

### Poste hors domaine

Exemple :

```text
WORKGROUP
```

Le poste n'est pas rattaché à un domaine Active Directory et utilise un groupe de travail local.

---

## 💡 Alternative PowerShell moderne

La commande `Get-WmiObject` est désormais remplacée progressivement par `Get-CimInstance`.

Équivalent recommandé :

```powershell
(Get-CimInstance Win32_ComputerSystem).Domain
```

---

## 🔎 Informations complémentaires

Pour obtenir plus d'informations sur l'état du poste :

```powershell
Get-CimInstance Win32_ComputerSystem | Select-Object Name, Domain, PartOfDomain
```

Exemple de résultat :

```text
Name        Domain              PartOfDomain
----        ------              ------------
PC-CLIENT01 entreprise.local    True
```

Le champ :

```text
PartOfDomain
```

indique directement si la machine appartient à un domaine Active Directory.
