# Activation du SSH sur un switch Cisco

## 📖 Description

Cette procédure permet d'activer l'accès distant en **SSH** sur un switch Cisco afin de remplacer les connexions Telnet non chiffrées.

> [!IMPORTANT]
> Il est recommandé d'utiliser **SSH version 2**, plus sécurisée que la version 1.

---

## 📋 Prérequis

- Accès au mode privilégié (`enable`)
- Accès au mode configuration (`configure terminal`)
- Nom de domaine défini
- Utilisateur administrateur créé

---

## ⚙️ Configuration

### 1. Définir le nom de domaine

Remplacer `<domaine.local>` par le nom de domaine de votre entreprise.

```bash
ip domain-name <domaine.local>
```

---

### 2. Créer un compte administrateur

Remplacer `<mdp>` par un mot de passe robuste.

```bash
username admin privilege 15 secret <mdp>
```

---

### 3. Générer la paire de clés RSA

```bash
crypto key generate rsa
```

Lorsque le switch demande la taille de la clé, saisir :

```text
2048
```

> [!TIP]
> Une clé RSA de **2048 bits** constitue le minimum recommandé aujourd'hui.

---

### 4. Activer SSH

```bash
ip ssh version 2

line vty 0 15
login local
transport input ssh
```

Cette configuration :

- active SSH version 2 ;
- utilise la base d'utilisateurs locale pour l'authentification ;
- autorise uniquement les connexions SSH sur les lignes VTY.

---

## ✅ Vérification

Afficher la configuration SSH :

```bash
show ip ssh
```

Afficher les utilisateurs configurés :

```bash
show running-config | include username
```

Afficher les sessions SSH actives :

```bash
show ssh
```