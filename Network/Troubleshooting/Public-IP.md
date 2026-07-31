# Afficher l'adresse IP publique

## 📖 Description

Cette procédure permet d'obtenir l'**adresse IP publique** utilisée par une machine lorsqu'elle communique avec Internet.

Cette information est notamment utile pour :

- Vérifier l'adresse IP fournie par un fournisseur d'accès Internet.
- Diagnostiquer un problème de VPN.
- Contrôler une configuration NAT ou une redirection de ports.
- Identifier l'adresse source visible depuis Internet.

---

## ⚙️ Récupérer l'adresse IP publique avec PowerShell

```powershell
Invoke-RestMethod -Uri "https://api.ipify.org"
```

Cette commande interroge le service **ipify** afin de retourner l'adresse IP publique associée à la connexion Internet actuelle.

Exemple de résultat :

```text
82.xxx.xxx.xxx
```

---

## 🔍 Afficher des informations détaillées sur l'adresse IP publique

```powershell
Invoke-RestMethod -Uri "https://ipinfo.io/json"
```

Retourne des informations complémentaires :

- Adresse IP publique.
- Fournisseur d'accès Internet (ISP).
- Localisation approximative.
- Organisation associée.

Exemple de résultat :

```json
{
  "ip": "82.xxx.xxx.xxx",
  "city": "Strasbourg",
  "country": "FR",
  "org": "ISP"
}
```

---

## 🌐 Alternatives en ligne de commande

### Avec curl

```powershell
curl https://api.ipify.org
```

---

### Avec DNS Cloudflare

```powershell
nslookup myip.opendns.com resolver1.opendns.com
```

Permet d'obtenir l'adresse IP publique via une requête DNS spécifique.

---

## ✅ Vérification

Comparer l'adresse retournée avec :

- L'interface WAN d'un routeur/firewall.
- La page d'administration de la box Internet.
- Une autre machine connectée au même réseau.

> [!NOTE]
> Plusieurs machines derrière une même box Internet auront généralement la même adresse IP publique, car elles utilisent une translation d'adresse (NAT).
