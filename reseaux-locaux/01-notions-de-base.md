# Notions de base des réseaux locaux

## Qu’est-ce qu’un réseau local?

Un **réseau local**, aussi appelé **LAN** (*Local Area Network*), permet de relier plusieurs appareils dans un même endroit, comme une maison, une école ou une entreprise.

Ces appareils peuvent être :

- Des ordinateurs.
- Des téléphones.
- Des imprimantes.
- Des serveurs.
- Des consoles de jeux.

Le réseau local permet aux appareils de communiquer entre eux, de partager des fichiers, d’imprimer des documents et d’accéder à Internet.

## Les appareils importants

### Commutateur

Un **commutateur**, souvent appelé **switch**, relie plusieurs appareils dans un même réseau local.

Par exemple, dans une salle de classe, plusieurs ordinateurs peuvent être branchés à un commutateur avec des câbles Ethernet. Le commutateur envoie les informations seulement à l’appareil concerné.

### Routeur

Un **routeur** relie différents réseaux entre eux. Dans une maison, il relie généralement le réseau local à Internet.

Le routeur peut aussi offrir d’autres services :

- Un serveur DHCP.
- Un pare-feu.
- Le Wi-Fi.
- Le NAT.

### Point d’accès Wi-Fi

Un **point d’accès Wi-Fi** permet aux appareils sans fil, comme les téléphones et les ordinateurs portables, de se connecter au réseau local.

Dans plusieurs maisons, le routeur et le point d’accès Wi-Fi sont combinés dans le même appareil.

## L’adresse IP

Une **adresse IP** (*Internet Protocol address*, ou adresse du protocole Internet) est un numéro attribué à chaque appareil qui se connecte à un réseau.

Cet appareil peut être :

- Un ordinateur.
- Un téléphone cellulaire.
- Une tablette.
- Une imprimante.
- Une console de jeux.
- Une télévision intelligente.
- Un réfrigérateur intelligent.
- Un routeur.

L’adresse IP permet d’identifier l’appareil sur le réseau et de lui envoyer des informations. C’est un peu comme une adresse postale : elle permet de savoir où envoyer les données.

### Adresse IPv4

L’**IPv4** (*Internet Protocol version 4*) est le format d’adresse IP le plus connu.

Une adresse IPv4 est composée de **quatre séries de chiffres**, séparées par des points. Chaque série peut aller de **0 à 255**.

Exemple :

```text
192.168.1.25
```

Autres exemples :

```text
10.0.0.5
172.16.10.20
192.168.0.100
```

Chaque appareil connecté à un réseau doit avoir une adresse IP pour pouvoir communiquer avec les autres appareils.

### Adresse IPv6

Comme le nombre d’adresses IPv4 disponibles est limité, un nouveau format a été créé : l’**IPv6** (*Internet Protocol version 6*).

Une adresse IPv6 est plus longue et utilise des chiffres ainsi que des lettres. Elle permet de créer beaucoup plus d’adresses que l’IPv4.

Exemple d’adresse IPv6 :

```text
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

### Adresse IP privée et publique

Il existe deux types d’adresses IP :

- **Adresse IP privée** : utilisée à l’intérieur d’un réseau local, comme `192.168.1.25`.
- **Adresse IP publique** : utilisée sur Internet et attribuée par le fournisseur Internet.

Plusieurs appareils d’un même réseau local peuvent avoir des adresses IP privées différentes, mais ils partagent souvent une seule adresse IP publique pour accéder à Internet.

### Vidéo explicative

[Regarder la vidéo : comprendre l’adresse IP](https://www.youtube.com/watch?v=Oc7Ts8tVjyE&t=4s)

## Le masque de sous-réseau

Le **masque de sous-réseau** indique quelle partie de l’adresse IP identifie le réseau et quelle partie identifie l’appareil.

Le masque le plus courant dans les petits réseaux est :

```text
255.255.255.0
```

Avec ce masque, les adresses comme `192.168.1.10`, `192.168.1.25` et `192.168.1.200` appartiennent généralement au même réseau local.

On écrit souvent ce réseau sous la forme :

```text
192.168.1.0/24
```

## La passerelle par défaut

La **passerelle par défaut** est habituellement l’adresse du routeur. C’est le chemin que prend un appareil pour communiquer avec un autre réseau, comme Internet.

Exemple courant :

```text
192.168.1.1
```

Si la passerelle est mal configurée, un appareil peut parfois communiquer avec les autres appareils du réseau local, mais ne pas réussir à accéder à Internet.

## Le serveur DNS

Le **DNS** (*Domain Name System*) traduit un nom de site Web en adresse IP.

Par exemple, lorsqu’une personne écrit `www.google.com` dans un navigateur, le serveur DNS trouve l’adresse IP correspondante pour permettre la connexion.

Sans serveur DNS, il faudrait connaître l’adresse IP de chaque site Web pour pouvoir le visiter.

## Le serveur DHCP

Un **serveur DHCP** (*Dynamic Host Configuration Protocol*) attribue automatiquement une adresse IP et les paramètres réseau nécessaires aux appareils qui se connectent au réseau.

Il peut fournir :

- Une adresse IP.
- Un masque de sous-réseau.
- Une passerelle par défaut.
- Des serveurs DNS.

Quand un appareil se connecte, il demande une configuration au serveur DHCP. Le serveur lui attribue alors une adresse IP disponible pour une durée limitée, appelée un **bail**.

### Plage DHCP

La **plage DHCP** est l’ensemble des adresses IP que le serveur peut attribuer automatiquement.

Par exemple, si le réseau est `192.168.1.0/24`, une plage DHCP pourrait être :

```text
192.168.1.100 à 192.168.1.200
```

Les adresses de la plage DHCP doivent appartenir au même sous-réseau que le réseau configuré.

## Le mode NAT

Le **NAT** (*Network Address Translation*) permet à plusieurs appareils d’un réseau privé d’accéder à Internet en utilisant une adresse IP publique commune.

Dans un contexte de virtualisation, une machine virtuelle en mode NAT reçoit une adresse IP privée dans un réseau virtuel. Lorsqu’elle accède à Internet, le routeur ou l’ordinateur hôte traduit son trafic.

Exemple :

- L’ordinateur hôte a l’adresse `192.168.1.25` sur le réseau local.
- La machine virtuelle reçoit une adresse comme `192.168.145.10` dans un réseau virtuel.
- Quand la VM accède à Internet, le NAT utilise l’adresse de l’hôte pour communiquer avec l’extérieur.

## Le pare-feu

Un **pare-feu** filtre le trafic réseau. Il décide quelles connexions sont autorisées à entrer ou à sortir du réseau.

Il aide à protéger un réseau contre :

- Les connexions non autorisées.
- Certains logiciels malveillants.
- Les attaques venant d’Internet.

Un pare-feu ne remplace pas les bonnes pratiques de sécurité, mais il constitue une protection importante.

## Vérifier sa configuration réseau

### Sur Windows

Ouvrir l’invite de commandes et entrer :

```text
ipconfig
```

Cette commande affiche notamment l’adresse IP, le masque de sous-réseau et la passerelle par défaut.

### Sur Linux

Ouvrir un terminal et entrer :

```text
ip a
```

Cette commande affiche les interfaces réseau et les adresses IP attribuées.

### Tester une connexion

La commande `ping` permet de vérifier si un autre appareil répond.

Exemple sur Windows :

```text
ping 192.168.1.1
```

Exemple sur Linux :

```text
ping 192.168.1.1
```

Si la réponse indique que des paquets sont reçus, la connexion entre les deux appareils fonctionne.

## Sécurité du réseau

La sécurité d’un réseau local repose sur plusieurs éléments :

- Un mot de passe Wi-Fi fort.
- Un pare-feu activé.
- Des mises à jour régulières des appareils.
- Des comptes utilisateurs avec des mots de passe différents.
- Un serveur DHCP correctement configuré.

Un serveur DHCP malveillant peut donner de mauvaises informations aux appareils, comme une fausse passerelle ou de faux serveurs DNS.

## À retenir

- Un **réseau local** relie des appareils dans une même zone.
- Le **commutateur** relie les appareils d’un même réseau.
- Le **routeur** relie différents réseaux, notamment le réseau local et Internet.
- L’**adresse IP** identifie un appareil sur un réseau.
- Une adresse **IPv4** contient quatre nombres allant de 0 à 255, séparés par des points.
- Le **masque de sous-réseau** définit les limites du réseau.
- La **passerelle par défaut** est généralement l’adresse du routeur.
- Le **DNS** traduit les noms de sites Web en adresses IP.
- Le **DHCP** attribue automatiquement les configurations réseau.
- Le **NAT** permet à plusieurs appareils d’un réseau privé d’accéder à Internet.
- Le **pare-feu** filtre le trafic pour protéger le réseau.
