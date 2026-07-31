# Mise à jour et diagnostic des GPO

## 📖 Description

Cette documentation regroupe les principales commandes permettant de mettre à jour les **stratégies de groupe (GPO)** et de vérifier leur bonne application sur un poste membre d'un domaine Active Directory.

> [!NOTE]
> Certaines commandes peuvent nécessiter l'ouverture d'une invite de commandes ou d'une console PowerShell en tant qu'administrateur.

---

## ⚙️ Mettre à jour les stratégies de groupe

### Mettre à jour uniquement les stratégies modifiées

```cmd
gpupdate
```

Cette commande applique uniquement les nouvelles stratégies ou celles ayant été modifiées depuis la dernière mise à jour.

---

### Forcer la réapplication de toutes les stratégies

```cmd
gpupdate /force
```

Cette commande réapplique l'ensemble des stratégies utilisateur et ordinateur, même si aucune modification n'a été détectée.

> [!TIP]
> Cette commande est particulièrement utile après la création ou la modification d'une GPO.

---

## 🔍 Vérifier les GPO appliquées

### Afficher les GPO appliquées à l'utilisateur

```cmd
gpresult /r /scope:user
```

Affiche les informations concernant l'utilisateur connecté, notamment les GPO appliquées.

---

### Afficher les GPO appliquées à l'ordinateur

```cmd
gpresult /r /scope:computer
```

Affiche les informations concernant l'ordinateur, notamment les GPO appliquées.

---

## 💡 Commandes complémentaires

### Générer un rapport HTML

```cmd
gpresult /h C:\Temp\GPReport.html
```

Génère un rapport HTML détaillé contenant l'ensemble des stratégies de groupe appliquées.

---

### Ouvrir le jeu de stratégie résultant (RSoP)

```cmd
rsop.msc
```

Ouvre la console **Resultant Set of Policy (RSoP)** permettant de visualiser graphiquement les stratégies effectivement appliquées.

---

## ✅ Vérification

Après l'exécution d'un `gpupdate`, vérifier que :

- Les nouvelles stratégies sont appliquées.
- Aucune erreur n'est affichée.
- Les GPO attendues apparaissent dans le résultat de `gpresult`.
