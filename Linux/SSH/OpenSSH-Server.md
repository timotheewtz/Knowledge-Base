# Installer et configurer un serveur OpenSSH sous Linux

## 📖 Description

**OpenSSH** est l'implémentation la plus répandue du protocole SSH (*Secure Shell*).

Il permet notamment de :

- Administrer un serveur à distance de manière sécurisée.

- Transférer des fichiers avec `scp` ou `sftp`.

- Utiliser l'authentification par mot de passe ou par clé SSH.

- Chiffrer l'ensemble des communications entre le client et le serveur.

Par défaut, le service écoute sur le **port 22/TCP**.

---

## 📋 Prérequis

- Une distribution Linux basée sur Debian/Ubuntu.

- Les privilèges `sudo`.

- Une connexion réseau entre le client et le serveur.

---

# 📦 Installer OpenSSH Server

Mettre à jour les paquets :

```bash
sudo apt update
```

Installer le serveur SSH :

```bash
sudo apt install openssh-server
```

---

# ▶️ Vérifier l'état du service

Afficher l'état du service :

```bash
sudo systemctl status ssh
```

Le démarrer si nécessaire :

```bash
sudo systemctl start ssh
```

L'activer au démarrage :

```bash
sudo systemctl enable ssh
```

Redémarrer le service :

```bash
sudo systemctl restart ssh
```

Recharger uniquement la configuration :

```bash
sudo systemctl reload ssh
```

---

# 🌐 Vérifier que le serveur écoute

Afficher les ports ouverts :

```bash
sudo ss -tulpn | grep ssh
```

ou

```bash
sudo ss -tulpn | grep :22
```

Le port **22/TCP** doit apparaître.

---

# ⚙️ Modifier la configuration SSH

Le fichier de configuration principal est :

```text
/etc/ssh/sshd_config
```

L'éditer avec :

```bash
sudo nano /etc/ssh/sshd_config
```

ou

```bash
sudo vim /etc/ssh/sshd_config
```

Après toute modification :

```bash
sudo systemctl restart ssh
```

---

# 🔧 Paramètres courants

## Changer le port SSH

Par défaut :

```text
Port 22
```

Exemple :

```text
Port 2222
```

---

## Autoriser ou interdire la connexion Root

Autoriser :

```text
PermitRootLogin yes
```

Interdire (recommandé) :

```text
PermitRootLogin no
```

---

## Activer ou désactiver l'authentification par mot de passe

Autoriser :

```text
PasswordAuthentication yes
```

Désactiver (recommandé avec des clés SSH) :

```text
PasswordAuthentication no
```

---

## Autoriser uniquement certains utilisateurs

```text
AllowUsers timothee admin
```

---

# 🔑 Se connecter au serveur

Connexion classique :

```bash
ssh utilisateur@192.168.1.10
```

Connexion sur un port personnalisé :

```bash
ssh -p 2222 utilisateur@192.168.1.10
```

---

# 📋 Vérifier la configuration SSH

Vérifier la configuration sans redémarrer le service :

```bash
sudo sshd -t
```

Si aucune erreur n'est affichée, la configuration est valide.

---

# 🔥 Autoriser SSH dans le pare-feu UFW

Autoriser le port SSH par défaut :

```bash
sudo ufw allow ssh
```

Ou un port personnalisé :

```bash
sudo ufw allow 2222/tcp
```

Vérifier les règles :

```bash
sudo ufw status
```

---

# 📄 Consulter les journaux SSH

Afficher les derniers événements :

```bash
sudo journalctl -u ssh
```

Suivre les connexions en temps réel :

```bash
sudo journalctl -fu ssh
```

---

# 🛠️ Bonnes pratiques

- Installer uniquement `openssh-server` sur les machines devant être administrées à distance.

- Désactiver la connexion du compte `root`.

- Privilégier l'authentification par clé SSH.

- Vérifier la configuration avec `sshd -t` avant de redémarrer le service.

- Modifier le port d'écoute ne remplace pas les bonnes pratiques de sécurité, mais peut réduire le bruit des scans automatisés.

- Protéger le serveur avec un pare-feu (`ufw` ou `iptables`) et maintenir OpenSSH à jour.

## 📚 Résumé des commandes

| Commande                          | Description                                     |
| --------------------------------- | ----------------------------------------------- |
| `sudo apt install openssh-server` | Installer OpenSSH Server                        |
| `sudo systemctl status ssh`       | Vérifier l'état du service                      |
| `sudo systemctl start ssh`        | Démarrer le service                             |
| `sudo systemctl enable ssh`       | Activer au démarrage                            |
| `sudo systemctl restart ssh`      | Redémarrer le service                           |
| `sudo nano /etc/ssh/sshd_config`  | Modifier la configuration                       |
| `sudo sshd -t`                    | Vérifier la syntaxe du fichier de configuration |
| `ssh utilisateur@ip`              | Se connecter au serveur                         |
| `ssh -p <port> utilisateur@ip`    | Se connecter sur un port personnalisé           |
| `sudo ss -tulpn \| grep ssh`      | Vérifier que le serveur écoute                  |
| `sudo journalctl -u ssh`          | Consulter les journaux du service               |

> [!TIP]  
> Pour une sécurité optimale, utilise une authentification par **clé SSH** plutôt que par mot de passe. Tu peux générer une paire de clés avec `ssh-keygen`, puis copier la clé publique sur le serveur à l'aide de `ssh-copy-id utilisateur@serveur`. Cela renforce considérablement la sécurité et simplifie les connexions.
