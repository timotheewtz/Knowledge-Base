# Microsoft Windows Malicious Software Removal Tool (MRT)

## 📖 Description

**MRT (Malicious Software Removal Tool)** est un outil de sécurité intégré à Windows permettant de détecter et supprimer certains logiciels malveillants courants.

> [!NOTE]
> MRT **ne remplace pas un antivirus** comme Microsoft Defender ou une solution de sécurité tierce. Il s'agit d'un outil de désinfection ponctuel mis à jour chaque mois via Windows Update.

---

## 📋 Prérequis

- Windows 10 ou Windows 11
- Ouvrir l'outil avec un compte administrateur (recommandé)

---

## ⚙️ Lancer Microsoft MRT

Depuis **Exécuter** (`Win + R`), l'invite de commandes ou PowerShell :

```cmd
mrt
```

L'assistant Microsoft s'ouvre et permet de choisir le type d'analyse à effectuer.

---

## 🔍 Types d'analyse

### Analyse rapide

Analyse les emplacements les plus sensibles du système où les logiciels malveillants sont généralement présents.

> [!TIP]
> Recommandée pour une vérification rapide du poste.

---

### Analyse complète

Analyse l'ensemble des disques et fichiers du système.

> [!IMPORTANT]
> Cette analyse peut durer plusieurs dizaines de minutes selon la capacité du disque et le nombre de fichiers présents.

---

### Analyse personnalisée

Permet de sélectionner un dossier ou un lecteur spécifique à analyser.

Pratique pour contrôler une clé USB ou un répertoire suspect.

---

## 🔎 Vérifier le rapport d'analyse

Une fois l'analyse terminée, le rapport est enregistré dans :

```text
C:\Windows\Debug\MRT.log
```

Ce fichier contient notamment :

- La date de l'analyse.
- Le type d'analyse effectué.
- Les menaces détectées.
- Les éventuelles actions réalisées.

---

## 💡 Bonnes pratiques

- Exécuter MRT en cas de comportement suspect du système.
- Compléter l'analyse avec **Microsoft Defender** ou un antivirus professionnel.
- Vérifier régulièrement que Windows Update est à jour afin de disposer de la dernière version de MRT.

> [!TIP]
> Pour une analyse plus approfondie, il est recommandé d'utiliser également **Microsoft Defender Offline** ou un antivirus spécialisé en complément.

---

## ✅ Vérification

À la fin de l'analyse :

- Vérifier que l'analyse s'est terminée sans erreur.
- Consulter le fichier `C:\Windows\Debug\MRT.log`.
- Redémarrer le poste si MRT ou Windows le recommande.
