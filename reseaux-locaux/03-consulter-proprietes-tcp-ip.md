# Consulter les propriétés TCP/IPv4 sous Windows

## Objectif

Accéder aux propriétés IPv4 de la carte réseau à partir du Centre Réseau et partage, sans modifier la configuration.

## 1. Ouvrir le Centre Réseau et partage

1. Ouvrir le menu Démarrer.
2. Rechercher `Panneau de configuration`.
3. Si le raccourci **Centre Réseau et partage** apparaît comme sur la capture, cliquer dessus. Sinon, ouvrir le Panneau de configuration, puis choisir **Réseau et Internet > Centre Réseau et partage** dans l’affichage par catégories.

![Accéder au Centre Réseau et partage](images/cmt-acceder-reseauetpartage.jpg)

## 2. Afficher les cartes réseau

1. Dans le menu de gauche, cliquer sur **Modifier les paramètres de la carte**.
2. Dans la fenêtre Connexions réseau, repérer la connexion à consulter : Ethernet pour une connexion câblée ou Wi-Fi pour une connexion sans fil.
3. Faire un clic droit sur cette connexion, puis choisir **Propriétés**.

![Modifier les paramètres de la carte réseau](images/modifier-param-carte-reseau.jpg)

## 3. Ouvrir les propriétés TCP/IPv4

1. Dans l’onglet **Gestion de réseau**, sélectionner la ligne **Version 4 du protocole Internet (TCP/IPv4)** sans décocher sa case.
2. Cliquer sur **Propriétés**.
3. La fenêtre des propriétés IPv4 s’ouvre.

![Propriétés de la carte Ethernet et du protocole TCP IPv4](images/Capture-decran-1.jpg)

## 4. Observer la configuration

La fenêtre permet de vérifier si les paramètres suivants sont obtenus automatiquement ou saisis manuellement :

- L’adresse IP.
- Le masque de sous-réseau.
- La passerelle par défaut.
- Les adresses des serveurs DNS.

Sur la capture, les options **Obtenir automatiquement une adresse IP** et **Obtenir automatiquement les adresses des serveurs DNS** sont sélectionnées. Les champs manuels sont donc grisés.

> Cette fenêtre montre le mode de configuration. Lorsque l’attribution est automatique, elle n’affiche pas les valeurs actuellement reçues. Pour les consulter, ouvrir l’invite de commandes et utiliser `ipconfig /all`.

## 5. Fermer sans modifier

Cliquer sur **Annuler** pour quitter les propriétés IPv4 sans appliquer de changement, puis fermer les autres fenêtres.

> Ne pas modifier les paramètres ni décocher TCP/IPv4 pour simplement les consulter. Une configuration incorrecte peut interrompre la connexion réseau.

## Captures à placer dans le dépôt

Pour afficher les illustrations, téléverser les trois fichiers fournis dans `reseaux-locaux/images/`, en conservant exactement ces noms :

- `cmt-acceder-reseauetpartage.jpg`
- `modifier-param-carte-reseau.jpg`
- `Capture-decran-1.jpg`
