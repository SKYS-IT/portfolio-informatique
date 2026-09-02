# Lab Active Directory

## Objectif

Déployer un environnement Active Directory permettant d'administrer des utilisateurs et des postes Windows au sein d'un domaine.

## Environnement

* VirtualBox
* Windows Server 2025
* Windows 11
* Active Directory Domain Services (AD DS)
* DNS
* DHCP
* Domaine : `lab.local`

## 1. Configuration des machines virtuelles

J'ai tout d'abord créé les machines virtuelles nécessaires à la réalisation du laboratoire dans VirtualBox.

J'ai configuré le réseau des machines virtuelles en utilisant le mode **Accès par pont** afin que les machines puissent communiquer avec le réseau et entre elles.

Les machines utilisées sont :

* Une machine virtuelle Windows Server 2025 destinée à servir de contrôleur de domaine.
* Une machine virtuelle Windows 11 destinée à servir de poste client.

## 2. Configuration réseau

Après avoir créé les machines virtuelles, j'ai configuré leur réseau afin de permettre la communication entre le serveur et le poste client.

Le serveur Windows Server 2025 a été configuré avec une **adresse IP statique**, nécessaire pour assurer correctement les services réseau et Active Directory.

J'ai ensuite vérifié la connectivité entre les différentes machines.

## 3. Installation d'Active Directory

J'ai installé le rôle **Active Directory Domain Services (AD DS)** sur Windows Server 2025.

J'ai ensuite promu le serveur en contrôleur de domaine et créé le domaine :

lab.local

## 4. Configuration du DNS

Le service DNS a été configuré afin de permettre la résolution des noms au sein du domaine lab.local.

J'ai effectué des tests de résolution afin de vérifier que le DNS fonctionnait correctement.

## 5. Configuration du DHCP

J'ai configuré le service DHCP afin d'attribuer automatiquement des paramètres réseau aux postes clients.

Le DHCP permet notamment de fournir :

* Une adresse IP
* Un masque de sous-réseau
* Une passerelle
* Un serveur DNS

## 6. Création des utilisateurs

J'ai créé plusieurs comptes utilisateurs dans Active Directory afin de tester l'authentification sur le domaine.

Les comptes créés sont notamment :

* `jmarie` — Jean Marie
* `mhenry` — Marc Henry

## 7. Intégration du poste Windows 11 au domaine

J'ai ensuite intégré le poste Windows 11 au domaine `lab.local`.

Une fois le poste intégré au domaine, j'ai redémarré la machine afin de pouvoir utiliser les comptes Active Directory.

## 8. Tests

### Test de connectivité

J'ai utilisé la commande `ping` afin de vérifier la communication entre les machines.

### Test DNS

J'ai utilisé la commande `nslookup` afin de vérifier la résolution DNS du domaine `lab.local`.

### Vérification de l'intégration au domaine

J'ai vérifié que le poste Windows 11 était bien membre du domaine `lab.local`.

### Authentification

J'ai testé la connexion à Windows 11 avec un compte utilisateur Active Directory.

### Vérification de l'utilisateur connecté

J'ai utilisé la commande :

`whoami`

afin de vérifier l'identité du compte connecté.

## 9. Difficultés rencontrées

Au cours du laboratoire, j'ai rencontré différentes difficultés liées à la connexion du domaine et au GPO. Dans la configuration du réseau il faut retirer la connectivité ipv6 pour que le poste client puisse directement communiquer sans embrouille au Domaine. J'ai rencontré un problème avec le GPO car suite a une mise à jour de sécurité Microsoft (MS16-072) il faut aller dans l'onglet délégations du gpo puis ajouter Utilisateurs Authentifiés et les faire Lire.
Ces problèmes m'ont permis de pratiquer le dépannage et de mieux comprendre les relations entre DNS, réseau, Active Directory et les postes clients.

## 10. Compétences acquises

Ce laboratoire m'a permis de développer des compétences pratiques en :

* VirtualBox
* Configuration réseau
* Adressage IP
* Windows Server
* Active Directory
* DNS
* DHCP
* Gestion des utilisateurs
* Gestion d'un domaine Windows
* Intégration d'un poste client à un domaine
* Dépannage réseau et système
* Commandes `ping`, `nslookup`, `whoami`, ipconfig /all, gpupdate /force 

## 11. Résultat

Le laboratoire a permis de mettre en place un environnement Windows fonctionnel avec un contrôleur de domaine Active Directory, un serveur DNS/DHCP et un poste Windows 11 intégré au domaine `lab.local`.

Les utilisateurs créés dans Active Directory peuvent s'authentifier sur le poste client du domaine.
