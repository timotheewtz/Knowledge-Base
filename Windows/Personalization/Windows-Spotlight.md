# Réinitialiser et réparer Windows Spotlight

## 📖 Description

Cette procédure permet de **réinitialiser Windows Spotlight (Windows À la une)** lorsqu'il ne fonctionne plus correctement.

Elle permet notamment de résoudre les problèmes suivants :

- Les images de l'écran de verrouillage ne changent plus.
- Windows Spotlight reste bloqué sur une même image.
- Les informations affichées sur l'écran de verrouillage disparaissent.
- Windows Spotlight ne se réactive plus après une mise à jour.

> [!IMPORTANT]
> Fermer la session ou redémarrer le PC une fois la procédure terminée afin de prendre en compte les modifications.

---

## 📋 Prérequis

- Windows 10 ou Windows 11
- Exécuter les commandes avec un compte administrateur

---

## ⚙️ Étape 1 - Supprimer le cache de Windows Spotlight

Supprimer le cache et les paramètres de Windows Spotlight :

```cmd
DEL /F /S /Q /A "%USERPROFILE%\AppData\Local\Packages\MicrosoftWindows.Client.CBS_cw5n1h2txyewy\LocalCache\Microsoft\IrisService"

DEL /F /S /Q /A "%USERPROFILE%\AppData\Local\Packages\Microsoft.Windows.ContentDeliveryManager_cw5n1h2txyewy\LocalCache\Microsoft\IrisService"

DEL /F /S /Q /A "%USERPROFILE%\AppData\Local\Packages\Microsoft.Windows.ContentDeliveryManager_cw5n1h2txyewy\LocalState\Assets"

DEL /F /S /Q /A "%USERPROFILE%\AppData\Local\Packages\Microsoft.Windows.ContentDeliveryManager_cw5n1h2txyewy\Settings"
```

Cette étape supprime :

- le cache des images ;
- les paramètres de Windows Spotlight ;
- les ressources téléchargées.

---

## ⚙️ Étape 2 - Réenregistrer Windows Spotlight

Réenregistrer **Content Delivery Manager** :

```powershell
PowerShell -ExecutionPolicy Unrestricted -Command "& {$manifest = (Get-AppxPackage *ContentDeliveryManager*).InstallLocation + '\AppxManifest.xml' ; Add-AppxPackage -DisableDevelopmentMode -Register $manifest}"
```

Réenregistrer **Microsoft Windows Client CBS** :

```powershell
PowerShell -ExecutionPolicy Unrestricted -Command "& {$manifest = (Get-AppxPackage *MicrosoftWindows.Client.CBS*).InstallLocation + '\AppxManifest.xml' ; Add-AppxPackage -DisableDevelopmentMode -Register $manifest}"
```

Ces commandes réinstallent les composants responsables du fonctionnement de Windows Spotlight sans réinstaller Windows.

---

## 🔄 Étape 3 - Redémarrer le poste

Redémarrer Windows ou fermer puis rouvrir la session utilisateur.

Une fois reconnecté :

1. Ouvrir **Paramètres**.
2. Accéder à **Personnalisation** → **Écran de verrouillage**.
3. Vérifier que **À la une Windows (Windows Spotlight)** est bien sélectionné.

---

## ✅ Vérification

Après le redémarrage :

- Les images de l'écran de verrouillage changent à nouveau.
- Les informations Windows Spotlight sont affichées.
- Les nouvelles images sont téléchargées automatiquement.

---

> [!TIP]
> Si le problème persiste, désactiver Windows Spotlight, redémarrer le poste, puis le réactiver avant de relancer cette procédure.

---

## 💡 Informations complémentaires

Windows Spotlight repose principalement sur les composants :

- `Microsoft.Windows.ContentDeliveryManager`
- `MicrosoftWindows.Client.CBS`

La suppression de leur cache suivie de leur réenregistrement permet généralement de résoudre la majorité des dysfonctionnements liés à l'écran de verrouillage.
