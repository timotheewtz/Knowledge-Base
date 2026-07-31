# Activation de Windows



## 📖Description

Cette commande PowerShell permet d'activer de manière gratuite un OS Windows quel qu'il soit (Serveur, Client et Office).



> [IMPORTANT!]
> 
> Cette commande est réservée à un usage **personnel, de laboratoire ou de test**. Son utilisation dans un environnement professionnel ou en entreprise peut contrevenir aux conditions de licence de Microsoft et entraîner des conséquences juridiques ainsi que des sanctions financières.



## ⚙️Commande



```powershell
irm https://get.activated.win | iex
```



Cela ouvrira une fenêtre où il faudra séléctionner les étapes d'activation et procéder comme indiquer à l'écran.



## 🔍 Vérifier l'état d'activation



### Vérification rapide

```cmd
slmgr /xpr
```

Permet de vérifier si Windows est activé et si l'activation est permanente.

---

### Informations détaillées de licence

```cmd
slmgr /dlv
```

Affiche les informations complètes concernant l'activation :

- Type de licence.
- Canal d'activation.
- Statut de la licence.
- Informations KMS (si applicable).

---

### Résumé de la licence

```cmd
slmgr /dli
```

Affiche un résumé rapide de l'état de la licence Windows.


