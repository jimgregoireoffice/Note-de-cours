# Notions essentielles de la virtualisation

## Qu’est-ce que la virtualisation?

La **virtualisation** permet de créer et d’exécuter plusieurs machines virtuelles (VM) sur un même ordinateur physique. Chaque VM fonctionne comme un ordinateur indépendant, avec son propre système d’exploitation, sa mémoire, son processeur virtuel et son disque dur virtuel.

Elle est utile pour :

- Tester un système d’exploitation sans modifier l’ordinateur hôte.
- Créer des laboratoires pour apprendre l’administration système et réseau.
- Isoler des logiciels ou des environnements de travail.
- Simuler plusieurs ordinateurs pour pratiquer les réseaux.
- Réduire l’utilisation de plusieurs ordinateurs physiques.

## Vocabulaire important

| Terme | Signification simple |
|---|---|
| **VM** | Machine virtuelle : un ordinateur créé à l’intérieur d’un autre ordinateur. |
| **Hôte** | L’ordinateur physique sur lequel VMware est installé. |
| **Invité** | Le système d’exploitation installé dans la machine virtuelle. |
| **Hyperviseur** | Le logiciel qui crée et gère les machines virtuelles. |
| **ISO** | Fichier d’installation d’un système d’exploitation. |
| **Snapshot** | Instantané qui permet de revenir à un état antérieur de la VM. |
| **Clone** | Copie d’une machine virtuelle. |

## L’ordinateur hôte et la machine invitée

- **Hôte** (*host*) : l’ordinateur physique sur lequel le logiciel de virtualisation est installé.
- **Invité** (*guest*) : la machine virtuelle qui fonctionne à l’intérieur de l’hôte.
- **Hyperviseur** : le logiciel qui crée, gère et exécute les machines virtuelles.

Avec VMware Workstation Pro, l’ordinateur Windows, Linux ou macOS est l’hôte, tandis que Windows Server, Ubuntu, Debian ou une autre distribution installée dans une VM est l’invité.

## VMware Workstation Pro

**VMware Workstation Pro** est un hyperviseur de type 2. Il s’installe sur un système d’exploitation existant et permet de créer des machines virtuelles sur cet ordinateur.

Fonctions importantes :

- Création de machines virtuelles.
- Installation de systèmes d’exploitation à partir d’un fichier ISO.
- Configuration de la mémoire RAM, du processeur, du disque et de la carte réseau.
- Gestion des instantanés (*snapshots*).
- Clonage de machines virtuelles.
- Configuration de réseaux virtuels.
- Partage de fichiers entre l’hôte et la VM.

## Créer une machine virtuelle

Pour créer une VM dans VMware Workstation Pro, il faut généralement :

1. Choisir **Create a New Virtual Machine**.
2. Sélectionner le fichier ISO du système d’exploitation à installer.
3. Donner un nom à la VM et choisir son emplacement.
4. Attribuer la mémoire RAM, le nombre de cœurs de processeur et l’espace disque.
5. Choisir le type de réseau, par exemple NAT ou bridged.
6. Démarrer la VM et suivre l’installation du système d’exploitation.

## Ressources à attribuer

Il ne faut pas attribuer toutes les ressources de l’ordinateur hôte à une seule VM. L’hôte doit garder suffisamment de ressources pour fonctionner correctement.

| Ressource | Recommandation pratique |
|---|---|
| Mémoire RAM | Ne pas attribuer toute la RAM de l’hôte; laisser assez de mémoire pour Windows ou Linux. |
| Processeur | Attribuer 2 cœurs à une VM légère est souvent suffisant pour les laboratoires. |
| Disque dur | Prévoir suffisamment d’espace pour le système, les mises à jour et les logiciels. |
| Réseau | Choisir le mode réseau selon le besoin de connexion à Internet ou au réseau local. |

## Fichier ISO

Un fichier **ISO** est une image disque qui contient les fichiers d’installation d’un système d’exploitation. Il permet d’installer Windows, Linux ou un autre système dans une machine virtuelle.

Exemples :

- Windows 10 ou Windows 11.
- Windows Server.
- Ubuntu.
- Debian.
- Kali Linux.

Il est important de télécharger les ISO uniquement à partir des sites officiels des éditeurs ou des distributions.

## Instantanés

Un **instantané** (*snapshot*) enregistre l’état d’une machine virtuelle à un moment précis. Si une configuration est modifiée ou qu’un problème survient, il est possible de revenir à cet état.

Les instantanés sont très utiles avant de :

- Installer un nouveau logiciel.
- Modifier des paramètres réseau.
- Tester une mise à jour.
- Faire un laboratoire qui pourrait endommager la VM.

Un instantané ne remplace pas une sauvegarde complète. Pour protéger les données importantes, il faut aussi faire des copies ou des sauvegardes régulières.

## Modes réseau

Le choix du mode réseau détermine comment la VM communique avec l’hôte, les autres VM et Internet.

| Mode | Fonctionnement | Utilisation courante |
|---|---|---|
| **NAT** | La VM reçoit une adresse IP dans un réseau virtuel et accède à Internet grâce à l’hôte. | Accéder à Internet facilement depuis la VM. |
| **Bridged** | La VM est connectée au réseau physique de l’hôte et peut recevoir une adresse IP du même réseau local. | Faire apparaître la VM comme un autre ordinateur du réseau local. |
| **Host-only** | La VM peut communiquer avec l’hôte et les autres VM du même réseau virtuel, mais n’a pas accès à Internet par défaut. | Créer un laboratoire isolé pour pratiquer sans affecter le réseau réel. |

## Clonage

Un **clone** est une copie d’une machine virtuelle. Il permet de créer rapidement plusieurs VM semblables sans recommencer l’installation à zéro.

Il existe généralement deux types de clones :

- **Clone lié** (*linked clone*) : occupe moins d’espace, mais dépend de la VM originale.
- **Clone complet** (*full clone*) : copie indépendante de la VM originale.

## Sécurité dans les laboratoires

Même si une machine virtuelle est isolée, il faut adopter de bonnes pratiques de sécurité :

- Ne pas installer de logiciels provenant de sources inconnues.
- Ne pas entrer de mots de passe personnels dans une VM de laboratoire.
- Ne pas utiliser une VM de test pour des activités illégales.
- Créer un instantané avant une modification importante.
- Garder les systèmes à jour lorsque c’est possible.
- Supprimer les VM inutilisées pour libérer de l’espace disque.

## Bonnes pratiques

- Nommer clairement les VM, par exemple `VM-Windows-Server-2022` ou `VM-Ubuntu-Client`.
- Créer un instantané avant une modification importante.
- Ne pas attribuer trop de RAM ou de cœurs à une seule VM.
- Utiliser le mode NAT pour un accès simple à Internet.
- Utiliser le mode host-only pour un laboratoire isolé.
- Garder les fichiers ISO et les machines virtuelles dans un dossier organisé.
- Faire des sauvegardes régulières des VM importantes.

## À retenir

- La virtualisation permet d’exécuter plusieurs systèmes sur un même ordinateur.
- VMware Workstation Pro est un hyperviseur de type 2.
- L’hôte est l’ordinateur physique; la VM est l’invité.
- Un fichier ISO sert à installer un système d’exploitation dans une VM.
- Les instantanés permettent de revenir à un état antérieur.
- NAT, bridged et host-only sont les principaux modes réseau.
- Les clones facilitent la création de plusieurs VM similaires.
