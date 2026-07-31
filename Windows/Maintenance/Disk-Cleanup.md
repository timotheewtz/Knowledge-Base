# Nettoyage et maintenance du disque sous Windows

## 📖 Description

Windows intègre plusieurs outils permettant de libérer de l'espace disque, supprimer les fichiers temporaires et maintenir le système en bon état de fonctionnement.

> [!NOTE]
> Certaines commandes nécessitent l'ouverture d'une invite de commandes ou d'une console PowerShell en tant qu'administrateur.

---

## 🧹 Nettoyage de disque

### Ouvrir l'utilitaire de nettoyage

```cmd
cleanmgr
```

Ouvre l'outil **Nettoyage de disque**, qui permet notamment de supprimer :

- Les fichiers temporaires
- Le contenu de la Corbeille
- Les miniatures (thumbnails)
- Les journaux d'erreurs Windows
- Les fichiers d'installation temporaires
- Les anciens fichiers Windows Update
- Les fichiers système inutilisés

> [!TIP]
> Cliquer sur **Nettoyer les fichiers système** permet d'accéder à des options supplémentaires, comme la suppression des anciennes mises à jour Windows.



## Vérifier et réparer le disque



### Vérifier le disque au prochain redémarrage



```cmd
chkdsk C: /f /r
```



Analyse le disque dur ou le SSD afin de :



- Détecter les erreurs du système de fichiers.
- Réparer automatiquement les erreurs détectées (`/f`).
- Localiser les secteurs défectueux et tenter de récupérer les données lisibles (`/r`).

> [!IMPORTANT]
> Si le lecteur est en cours d'utilisation (généralement le lecteur système `C:`), Windows proposera d'effectuer l'analyse au prochain redémarrage. Répondre **O** puis redémarrer le poste.



### Vérifier un disque sans effectuer de réparation

```cmd
chkdsk C:
```

Analyse le disque et affiche les éventuelles erreurs sans apporter de modification.

> [!TIP]
> Utiliser cette commande comme premier diagnostic avant de lancer une réparation complète avec `/f /r`.



---



## ⚙️ Nettoyage du magasin de composants Windows

```cmd
DISM /Online /Cleanup-Image /StartComponentCleanup
```

Supprime les anciennes versions des composants Windows afin de réduire l'espace disque utilisé.

> [!IMPORTANT]
> Cette commande est sans risque et recommandée après plusieurs mises à jour importantes de Windows.

---

## 🔍 Vérifier et réparer les fichiers système

```cmd
sfc /scannow
```

Analyse les fichiers système protégés et remplace automatiquement ceux qui sont corrompus.

---

## 🔧 Réparer l'image Windows

```cmd
DISM /Online /Cleanup-Image /RestoreHealth
```

Analyse et répare l'image du système Windows en téléchargeant les fichiers nécessaires depuis Windows Update si besoin.

Cette commande est souvent utilisée avant de relancer :

```cmd
sfc /scannow
```

---

## 📂 Ouvrir le dossier des fichiers temporaires

### Fichiers temporaires de l'utilisateur

```cmd
%temp%
```

---

### Fichiers temporaires du système

```cmd
temp
```

Permet d'accéder rapidement aux dossiers contenant les fichiers temporaires pouvant être supprimés (hors fichiers en cours d'utilisation).

---

## 🗑️ Optimiser le stockage

Ouvrir directement les paramètres de stockage de Windows :

```cmd
start ms-settings:storagesense
```

Permet de configurer **Storage Sense (Assistant Stockage)** afin d'automatiser le nettoyage des fichiers temporaires et de la Corbeille.

---

## ✅ Bonnes pratiques

- Exécuter régulièrement `cleanmgr` sur les postes peu utilisés.
- Utiliser `DISM /StartComponentCleanup` après les mises à jour majeures de Windows.
- En cas de problème système, exécuter d'abord :

```cmd
DISM /Online /Cleanup-Image /RestoreHealth
```

Puis :

```cmd
sfc /scannow
```

- Vider régulièrement les dossiers temporaires lorsque ceux-ci occupent un espace disque important.
