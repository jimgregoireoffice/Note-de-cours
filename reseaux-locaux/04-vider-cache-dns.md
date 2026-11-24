# Vider le cache DNS avec ipconfig /flushdns

## À quoi sert le cache DNS?

Le DNS permet de trouver l’adresse IP associée à un nom de domaine. Windows conserve temporairement les résultats dans un cache DNS local pour éviter de refaire la même recherche à chaque utilisation. Ce cache peut aussi mémoriser des échecs de résolution.

## Que fait la commande?

```cmd
ipconfig /flushdns
```

Cette commande vide et réinitialise le cache du résolveur DNS de Windows. Elle supprime les entrées ajoutées dynamiquement, y compris les réponses négatives (échecs mémorisés). Les prochaines recherches concernées pourront donc interroger de nouveau le serveur DNS.

## Pourquoi est-ce utile?

- **Adresse devenue périmée** : si l’adresse IP d’un site ou d’un serveur a changé, supprimer l’ancienne réponse locale permet de demander une réponse à jour au serveur DNS.
- **Échec mémorisé** : Windows peut avoir conservé une réponse indiquant qu’un nom n’existe pas. Vider le cache permet de réessayer sans attendre l’expiration de cette entrée, une fois le problème corrigé.
- **Dépannage DNS** : cela permet d’écarter une ancienne réponse locale lorsqu’un site ou un serveur n’est plus accessible par son nom.

### Exemple

Un serveur de fichiers a changé d’adresse IP, mais l’ordinateur utilise encore l’ancienne réponse conservée en cache. Après `ipconfig /flushdns`, une nouvelle recherche peut obtenir l’adresse actuelle, à condition que le serveur DNS fournisse la bonne information.

## Procédure sous Windows

1. Ouvrir le menu Démarrer et rechercher `cmd`.
2. Ouvrir l’invite de commandes. Si Windows indique que des droits supplémentaires sont nécessaires, la rouvrir avec **Exécuter en tant qu’administrateur**.
3. Entrer la commande suivante, puis appuyer sur Entrée :

```cmd
ipconfig /flushdns
```

4. Vérifier que Windows confirme que le cache de résolution DNS a été vidé.
5. Réessayer d’accéder au site ou au serveur concerné.

## Afficher le cache DNS

Pour consulter son contenu avant ou après l’opération :

```cmd
ipconfig /displaydns
```

## Limites importantes

- La commande ne change pas l’adresse IP de l’ordinateur et ne renouvelle pas son bail DHCP.
- Elle ne vide pas le cache du serveur DNS ni tous les caches propres aux applications ou aux navigateurs.
- Elle ne corrige pas une panne de connexion ni une mauvaise configuration du serveur DNS.
- Les entrées provenant du fichier local `hosts` ne sont pas éliminées par cette opération.
- Ce n’est pas une commande à exécuter systématiquement : le cache est normalement utile et se reconstruit au fil des recherches.

## À retenir

`ipconfig /flushdns` sert à vider le cache DNS local pour faciliter le dépannage de la résolution des noms. Ce n’est pas une commande pour changer son adresse IP ou accélérer systématiquement Internet.

## Source

[Microsoft Learn — ipconfig](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ipconfig)
