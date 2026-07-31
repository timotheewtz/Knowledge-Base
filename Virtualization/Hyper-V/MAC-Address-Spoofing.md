# Activer le MAC Address Spoofing sur une VM Hyper-V

## 📖 Description

Le **MAC Address Spoofing** permet à une machine virtuelle Hyper-V d'utiliser une adresse MAC différente de celle attribuée par défaut par l'hyperviseur.

Cette fonctionnalité est principalement utilisée dans les cas suivants :

- Utilisation d'équipements réseau virtuels dans une VM.
- Déploiement de firewalls ou routeurs virtuels (pfSense, OPNsense, FortiGate...).
- Configuration de solutions nécessitant plusieurs interfaces réseau virtuelles.
- Mise en place de laboratoires réseau avancés.

> [!NOTE]
> Par défaut, Hyper-V bloque les paquets utilisant une adresse MAC différente de celle attribuée à la carte réseau virtuelle afin d'éviter certains comportements réseau non désirés.

---

## 📋 Prérequis

- Hyper-V installé.
- Accès administrateur sur l'hôte Hyper-V.
- Machine virtuelle arrêtée avant modification recommandée.

---

## 🔍 Vérifier les machines virtuelles disponibles

Afficher la liste des machines virtuelles présentes sur l'hôte :

```powershell
Get-VM
```

Identifier le nom exact de la VM concernée.

---

## ⚙️ Activer le MAC Address Spoofing

Activer le spoofing d'adresse MAC sur l'adaptateur réseau virtuel :

```powershell
Get-VMNetworkAdapter -VMName "<nom de la VM>" | Set-VMNetworkAdapter -MacAddressSpoofing On
```

Remplacer :

```text
<nom de la VM>
```

par le nom réel de la machine virtuelle.

Exemple :

```powershell
Get-VMNetworkAdapter -VMName "Firewall-LAB" | Set-VMNetworkAdapter -MacAddressSpoofing On
```

---

## 🔒 Désactiver le MAC Address Spoofing

Pour revenir au comportement par défaut :

```powershell
Get-VMNetworkAdapter -VMName "<nom de la VM>" | Set-VMNetworkAdapter -MacAddressSpoofing Off
```

---

## ✅ Vérification

Vérifier l'état actuel de la configuration :

```powershell
Get-VMNetworkAdapter -VMName "<nom de la VM>" | Select-Object VMName, MacAddressSpoofing
```

Résultat attendu :

```text
VMName          MacAddressSpoofing
------          ------------------
Firewall-LAB    On
```

---

## 💡 Cas d'utilisation courants

### Firewall virtuel

Exemple :

Une VM pfSense possède plusieurs interfaces réseau :

- WAN
- LAN
- DMZ

Le MAC Address Spoofing peut être nécessaire pour permettre au firewall virtuel de gérer correctement les communications réseau.

---

### Laboratoire réseau

Utilisé dans les environnements de test pour simuler :

- Plusieurs équipements réseau.
- Des architectures complexes.
- Des environnements de production.

---

> [!WARNING]
> Éviter d'activer cette option sans nécessité sur des machines virtuelles classiques. Elle peut permettre à une VM d'usurper une adresse MAC et provoquer des comportements réseau inattendus.
