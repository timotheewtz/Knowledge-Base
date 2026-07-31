# Installation de l'agent Action1

## 📖 Description

**Action1** est une solution de gestion des postes permettant notamment :

- Le déploiement d'agents sur les machines.
- La gestion des mises à jour Windows et logiciels.
- L'inventaire matériel et logiciel.
- L'exécution de commandes à distance.
- La supervision des postes.

L'installation de l'agent permet d'intégrer un poste Windows dans la console Action1 afin de pouvoir l'administrer à distance.

---

## 📋 Prérequis

- Poste Windows compatible.
- Droits administrateur local.
- Connexion Internet.
- Accès à la console Action1.
- PowerShell lancé avec des privilèges administrateur.

---

# ⚙️ Installation automatique de l'agent

La commande suivante permet :

1. De télécharger le package MSI de l'agent.
2. D'effectuer une installation silencieuse.
3. D'attendre la fin de l'installation avant de terminer.

```powershell
curl -o "action1_agent.msi" "https://app.eu.action1.com/agent/<URL_AGENT>/Windows/agent.msi"; if ($?) { Start-Process msiexec -ArgumentList '/i "action1_agent.msi" /quiet /qn' -Wait }
```

---

## 🔎 Explication de la commande

### Téléchargement de l'agent

```powershell
curl -o "action1_agent.msi" "<URL_AGENT>"
```

Télécharge le fichier d'installation MSI depuis la console Action1.

---

### Installation silencieuse

```powershell
Start-Process msiexec -ArgumentList '/i "action1_agent.msi" /quiet /qn' -Wait
```

Options utilisées :

| Paramètre | Description                                        |
| --------- | -------------------------------------------------- |
| `/i`      | Installation du package MSI                        |
| `/quiet`  | Installation sans interface graphique              |
| `/qn`     | Mode totalement silencieux                         |
| `-Wait`   | Attend la fin de l'installation avant de continuer |

---

# 🔍 Vérification de l'installation

## Vérifier la présence du service Action1

Depuis PowerShell :

```powershell
Get-Service | Where-Object {$_.Name -like "*Action1*"}
```

Le service doit apparaître comme démarré.

---

## Vérifier dans la console Action1

Après installation :

1. Ouvrir la console Action1.
2. Vérifier que le poste apparaît dans la liste des endpoints.
3. Contrôler que l'agent communique correctement.

---

# 🛠️ Déploiement en masse

Cette méthode peut être utilisée dans un contexte de déploiement automatisé via :

- GPO Active Directory.
- Intune.
- Scripts PowerShell.
- Outils RMM.
- Solutions de gestion de parc.

---

# ⚠️ Points d'attention

> [!WARNING]
> L'URL de téléchargement de l'agent est généralement unique à l'organisation. Ne pas publier publiquement une URL contenant un identifiant d'environnement réel.

> [!IMPORTANT]
> Tester l'installation sur un poste pilote avant un déploiement massif afin de vérifier la communication avec la console et les éventuelles restrictions réseau.

---

# 💡 Bonnes pratiques

- Renommer les scripts avec un nom générique.
- Stocker les scripts d'installation dans un dossier dédié :

```text
Scripts
└── Deployment
    └── Action1
        └── Install-Agent.ps1
```

- Documenter la méthode de désinstallation en complément.
