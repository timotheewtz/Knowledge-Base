# Nettoyage du magasin de composants WinSxS

## 📖 Description

Le dossier **WinSxS (Windows Side-by-Side)** contient les composants nécessaires au fonctionnement de Windows, notamment :

- Les anciennes versions des composants système.
- Les fichiers nécessaires aux mises à jour Windows.
- Les éléments utilisés pour la réparation du système.

Avec le temps, ce dossier peut devenir volumineux à cause de l'accumulation des anciennes versions de composants.

L'outil **DISM (Deployment Image Servicing and Management)** permet d'analyser et de nettoyer ce magasin de composants.

> [!NOTE]
> La taille affichée du dossier WinSxS peut être trompeuse, car Windows utilise des liens physiques. Il est recommandé d'utiliser DISM pour analyser son occupation réelle.

---

## 📋 Prérequis

- Windows 10 ou Windows 11.
- PowerShell ou Invite de commandes ouverte en administrateur.
- Droits administrateur local.

---

# 🔍 Analyser le magasin de composants

Avant tout nettoyage, analyser l'état du magasin :

```cmd
Dism.exe /Online /Cleanup-Image /AnalyzeComponentStore
```

Cette commande affiche notamment :

- La taille réelle du magasin WinSxS.
- Le nombre de packages récupérables.
- L'espace disque potentiellement libérable.
- La date du dernier nettoyage effectué.

---

# 🧹 Nettoyer le dossier WinSxS

## Nettoyage standard

```cmd
Dism.exe /Online /Cleanup-Image /StartComponentCleanup
```

Cette commande supprime les anciennes versions des composants Windows qui ne sont plus nécessaires.

Elle permet notamment de :

- Réduire la taille du magasin WinSxS.
- Supprimer les anciens composants remplacés par des mises à jour plus récentes.
- Libérer de l'espace disque.

---

## Nettoyage avancé avec suppression des anciennes bases

```cmd
Dism.exe /Online /Cleanup-Image /StartComponentCleanup /ResetBase
```

Cette commande effectue un nettoyage plus important en supprimant les anciennes versions remplacées des composants Windows.

> [!WARNING]
> L'utilisation de `/ResetBase` empêche la désinstallation des mises à jour Windows déjà installées. À utiliser uniquement lorsque l'on est certain de conserver l'état actuel du système.

---

# 🔍 Vérification après nettoyage

Après l'opération, relancer l'analyse :

```cmd
Dism.exe /Online /Cleanup-Image /AnalyzeComponentStore
```

Comparer :

- La taille du magasin WinSxS.
- L'espace récupérable.
- Le nombre de packages nettoyables.

---

# 💡 Bonnes pratiques

- Toujours exécuter une analyse avant un nettoyage.
- Privilégier :

```cmd
Dism.exe /Online /Cleanup-Image /StartComponentCleanup
```

avant d'utiliser :

```cmd
Dism.exe /Online /Cleanup-Image /StartComponentCleanup /ResetBase
```

- Effectuer un nettoyage après une migration ou une mise à niveau majeure de Windows.
- Éviter de supprimer manuellement le contenu du dossier :

```text
C:\Windows\WinSxS
```

> [!IMPORTANT]
> Le dossier WinSxS ne doit jamais être vidé manuellement. Cela peut rendre Windows instable ou empêcher certaines réparations système.
