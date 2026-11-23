# DHCP, NAT, routeur et pare-feu

## Serveur DHCP

Un **serveur DHCP** (*Dynamic Host Configuration Protocol*) attribue automatiquement une adresse IP et les paramètres réseau nécessaires aux appareils qui se connectent à un réseau.

Il peut fournir :

- Une adresse IP
- Un masque de sous-réseau
- Une passerelle par défaut
- Des serveurs DNS

Quand un appareil se connecte, il demande une configuration au serveur DHCP. Le serveur lui attribue alors une adresse IP disponible pour une durée limitée, appelée un **bail**.

## Modifier la plage DHCP

Pour modifier manuellement les paramètres du DHCP, il faut d’abord modifier le **sous-réseau IP** afin qu’il corresponde aux adresses IP de début et de fin configurées dans la plage DHCP.

Par exemple, si la plage DHCP commence à `192.168.1.100` et se termine à `192.168.1.200`, le sous-réseau doit être compatible avec ces adresses, par exemple `192.168.1.0/24`.

## Adresse IP

Une **adresse IP** permet d’identifier un appareil sur un réseau.

Exemple : `192.168.1.25`

Il existe des adresses IP privées, utilisées dans un réseau local, et des adresses IP publiques, utilisées sur Internet.

## Mode NAT

En mode **NAT** (*Network Address Translation*), la machine virtuelle reçoit une adresse IP privée dans un réseau virtuel distinct.

Elle peut accéder à Internet, mais elle utilise l’adresse IP de l’ordinateur hôte pour communiquer avec l’extérieur. Elle ne reçoit donc pas directement une adresse IP sur le réseau local.

Exemple :

- L’ordinateur hôte a l’adresse `192.168.1.25` sur le réseau local.
- La VM reçoit une adresse comme `192.168.145.10` dans un réseau virtuel.
- Quand la VM va sur Internet, le NAT traduit son trafic en utilisant l’adresse de l’hôte.

## Routeur

Le **routeur** relie différents réseaux entre eux. Dans une maison ou une petite entreprise, il relie généralement le réseau local à Internet.

Il peut aussi inclure plusieurs services :

- NAT
- Serveur DHCP
- Pare-feu
- Wi-Fi

## Pare-feu

Un **pare-feu** filtre le trafic réseau. Il décide quelles connexions sont autorisées à entrer ou sortir du réseau.

C’est un élément important de la sécurité, car il peut bloquer du trafic malveillant venant d’Internet.

## Sécurité du réseau

La sécurité d’un réseau repose surtout sur le **routeur** et le **pare-feu**, qui contrôlent le trafic entre le réseau local et Internet.

Le serveur DHCP participe aussi à la sécurité parce qu’il attribue les configurations réseau. Toutefois, un serveur DHCP malveillant peut donner de mauvaises informations aux appareils, comme une fausse passerelle ou de faux serveurs DNS.

## À retenir

- Le **DHCP** attribue automatiquement les configurations réseau.
- Pour modifier la plage DHCP, le sous-réseau doit correspondre aux adresses de début et de fin.
- Le **NAT** permet à une VM d’accéder à Internet par l’hôte.
- Le **routeur** achemine le trafic entre les réseaux.
- Le **pare-feu** filtre le trafic pour protéger le réseau.
- Un serveur DHCP malveillant peut créer des risques de sécurité.
