# Activer la virtualisation imbriquée Hyper-V

## 📖 Description

La **virtualisation imbriquée (Nested Virtualization)** permet d'exécuter des fonctionnalités de virtualisation à l'intérieur d'une machine virtuelle Hyper-V.

Elle est notamment utilisée pour :

- Exécuter Hyper-V dans une VM.
- Utiliser Docker Desktop dans une VM Windows.
- Tester des environnements de virtualisation en laboratoire.
- Créer des environnements de formation ou de test.

> [!IMPORTANT]
> Cette fonctionnalité nécessite un processeur compatible avec la virtualisation matérielle (Intel VT-x ou AMD-V) et doit être activée au niveau du BIOS/UEFI de l'hôte physique.

---

## 📋 Prérequis

- Hyper-V installé sur l'hôte.
- Une machine virtuelle de génération 2 recommandée.
- Processeur compatible avec la virtualisation matérielle.
- VM arrêtée avant l'application de la configuration.

---

## 🔍 Vérifier les machines virtuelles disponibles

Afficher la liste des machines virtuelles Hyper-V :

```powershell
Get-VM
```

Cette commande permet de récupérer le nom exact de la VM à modifier.

---

## ⚙️ Activer la virtualisation imbriquée

Activer l'exposition des extensions de virtualisation matérielle pour une VM :

```powershell
Set-VMProcessor -VMName "<nom de la VM>" -ExposeVirtualizationExtensions $true
```

Remplacer :

```text
<nom de la VM>
```

par le nom réel de la machine virtuelle.

Exemple :

```powershell
Set-VMProcessor -VMName "LAB-DC01" -ExposeVirtualizationExtensions $true
```

---

## 🔄 Désactiver la virtualisation imbriquée

Pour désactiver la fonctionnalité :

```powershell
Set-VMProcessor -VMName "<nom de la VM>" -ExposeVirtualizationExtensions $false
```

---

## ✅ Vérification

Vérifier que la fonctionnalité est bien activée :

```powershell
Get-VMProcessor -VMName "<nom de la VM>" | Select-Object VMName, ExposeVirtualizationExtensions
```

Résultat attendu :

```text
VMName      ExposeVirtualizationExtensions
------      ------------------------------
LAB-DC01    True
```

---

## 💡 Bonnes pratiques

- Arrêter complètement la VM avant de modifier cette configuration.
- Réserver cette fonctionnalité aux environnements de test ou aux besoins spécifiques.
- Éviter de l'utiliser sur des machines virtuelles de production sans validation préalable.

> [!TIP]
> Après activation, un redémarrage complet de la machine virtuelle peut être nécessaire avant que les extensions de virtualisation soient disponibles dans l'OS invité.
