# Purger le spouleur d'impression Windows

## 📖 Description

Le service **Spouleur d'impression Windows (`Print Spooler`)** permet de gérer les travaux d'impression en attente avant leur envoi vers une imprimante.

Lorsqu'un problème survient, des fichiers d'impression peuvent rester bloqués dans la file d'attente et empêcher l'impression de nouveaux documents.

Cette procédure permet de :

- Arrêter temporairement le service d'impression.
- Supprimer les travaux d'impression bloqués.
- Redémarrer le service afin de rétablir le fonctionnement normal.

Cas d'utilisation :

- Documents bloqués dans la file d'impression.
- Imprimante affichée hors connexion malgré une connexion correcte.
- Erreurs répétées lors de l'impression.
- Service Print Spooler bloqué.

---

## 📋 Prérequis

- Session administrateur local.
- PowerShell lancé en administrateur.
- Aucun besoin de redémarrer la machine.

> [!WARNING]
> Cette procédure supprime tous les travaux d'impression actuellement en attente sur le poste.

---

# ⚙️ Purger la file d'impression

## 1. Arrêter le service Spouleur d'impression

```powershell
Stop-Service Spooler
```

Arrête le service Windows responsable de la gestion des impressions.

---

## 2. Supprimer les fichiers d'impression en attente

```powershell
Remove-Item "C:\Windows\System32\spool\PRINTERS\*.*" -Force
```

Supprime tous les fichiers temporaires présents dans le dossier du spouleur.

Ces fichiers correspondent aux travaux d'impression en attente.

---

## 3. Redémarrer le service Spouleur

```powershell
Start-Service Spooler
```

Redémarre le service d'impression afin de permettre de nouveaux travaux.

---

# 🔍 Vérification

Vérifier que le service est bien démarré :

```powershell
Get-Service Spooler
```

Résultat attendu :

```text
Status   Name
------   ----
Running  Spooler
```

---

# 🛠️ Alternative en ligne de commande

La même opération peut être réalisée avec l'invite de commandes :

Arrêter le service :

```cmd
net stop spooler
```

Supprimer les travaux :

```cmd
del /Q /F C:\Windows\System32\spool\PRINTERS\*.*
```

Redémarrer le service :

```cmd
net start spooler
```

---

# 💡 Bonnes pratiques

- Vérifier d'abord qu'il s'agit bien d'un problème de file d'impression avant de purger.
- Identifier l'imprimante concernée si plusieurs imprimantes sont configurées.
- Vérifier les pilotes d'impression en cas de problème récurrent.
- Éviter de purger régulièrement sans rechercher la cause du problème.

> [!TIP]
> Si le problème revient fréquemment, vérifier également :
> 
> - Les pilotes d'impression.
> - La connectivité réseau avec l'imprimante.
> - Les erreurs dans l'Observateur d'événements Windows.
> - Les mises à jour du serveur d'impression.
