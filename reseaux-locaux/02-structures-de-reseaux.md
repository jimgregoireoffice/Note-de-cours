# Structures de réseaux

Il existe deux grandes structures de réseaux : le réseau **pair-à-pair** et le réseau **client/serveur**.

## Réseau pair-à-pair

Le réseau **pair-à-pair**, aussi appelé **P2P** (*Peer-to-Peer*), permet à plusieurs appareils de communiquer directement entre eux, sans serveur central obligatoire.

Dans ce type de réseau, chaque appareil peut agir à la fois comme un **client** et comme un **serveur**. Par exemple, un ordinateur peut partager un dossier, tandis qu’un autre ordinateur peut y accéder.

Ce type de réseau est souvent utilisé par des particuliers à la maison. Il permet de connecter directement des appareils tels que :

- Un ordinateur.
- Un téléphone cellulaire.
- Une télévision intelligente.
- Une imprimante.
- Une console de jeux.

Il peut aussi être utilisé dans un petit bureau, lorsqu’il y a peu d’appareils et peu de besoins de gestion centralisée.

### Avantages

- Simple à mettre en place.
- Moins coûteux, car un serveur dédié n’est pas nécessaire.
- Convient bien à un petit nombre d’appareils.
- Permet de partager directement des fichiers et des ressources.

### Inconvénients

- La sécurité et la gestion des accès sont plus difficiles à centraliser.
- L’administration devient plus compliquée lorsque le nombre d’appareils augmente.
- Les fichiers partagés dépendent de l’appareil qui les héberge : si cet appareil est éteint, la ressource n’est plus disponible.
- Les sauvegardes doivent souvent être faites sur plusieurs appareils.
- Moins adapté aux organisations ayant plusieurs utilisateurs et beaucoup de données.

## Réseau client/serveur

Le réseau **client/serveur** utilise un ou plusieurs **serveurs** qui offrent des services à des appareils appelés **clients**.

Le client envoie une demande au serveur. Le serveur traite cette demande et renvoie une réponse.

Exemple : lorsqu’un ordinateur ouvre un site Web, il agit comme un client. Le serveur Web reçoit la demande et envoie la page Web à l’ordinateur.

Ce type de réseau est généralement utilisé par les organisations, notamment les petites, moyennes et grandes entreprises.

Un serveur peut offrir plusieurs services, tels que :

- Le partage de fichiers.
- La gestion des utilisateurs et des mots de passe.
- L’impression partagée.
- L’attribution automatique d’adresses IP avec DHCP.
- L’hébergement de sites Web.
- La sauvegarde centralisée des données.

### Avantages

- Les fichiers et les ressources sont centralisés.
- La gestion des utilisateurs, des accès et des permissions est plus facile.
- La sécurité peut être mieux contrôlée lorsque le réseau est bien configuré.
- Les sauvegardes sont plus faciles à organiser, car les données importantes peuvent être regroupées.
- Convient aux organisations avec plusieurs employés.

### Inconvénients

- Le coût est généralement plus élevé, car il faut acheter, configurer et entretenir un serveur.
- Une personne responsable de l’administration du réseau est souvent nécessaire.
- Si le serveur principal tombe en panne, certains services peuvent devenir indisponibles.
- La mise en place demande plus de connaissances techniques.

## Comparaison rapide

| Élément | Pair-à-pair | Client/serveur |
|---|---|---|
| Serveur central | Généralement non requis | Requis |
| Rôle des appareils | Chaque appareil peut être client et serveur | Le serveur offre des services; les clients les utilisent |
| Coût | Moins élevé | Plus élevé |
| Utilisation courante | Maison ou petit réseau | Entreprise ou organisation |
| Administration | Plus simple au début, mais plus difficile à grande échelle | Plus structurée et centralisée |
| Sécurité | Moins facile à gérer | Meilleure lorsqu’elle est bien configurée |
| Sauvegardes | Réparties sur plusieurs appareils | Plus faciles à centraliser |

## À retenir

- Le réseau **pair-à-pair** permet aux appareils de partager directement des ressources entre eux.
- Il est souvent utilisé à la maison, mais peut aussi convenir à un très petit bureau.
- Le réseau **client/serveur** utilise un serveur pour offrir des services aux clients.
- Il est généralement utilisé dans les entreprises et les organisations.
- Le réseau client/serveur coûte généralement plus cher, mais facilite la gestion centralisée, la sécurité et les sauvegardes.
