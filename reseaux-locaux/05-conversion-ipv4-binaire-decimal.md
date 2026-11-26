# Convertir une adresse IPv4 : décimal ↔ binaire

Une adresse IPv4 est écrite avec des nombres décimaux (de 0 à 255), mais les ordinateurs et les équipements réseau la lisent en binaire, c’est-à-dire avec des 0 et des 1. Savoir passer d’un format à l’autre aide à comprendre les masques de sous-réseau, les plages DHCP et le découpage d’un réseau.

## 1. Les bases à connaître

Une adresse IPv4 compte **4 octets** séparés par des points. Un octet est un groupe de **8 bits**, et chaque bit vaut 0 (arrêté) ou 1 (allumé). Cela donne 32 bits au total.

```text
192      .168      .1        .25
11000000 .10101000 .00000001 .00011001
```

Un octet peut donc prendre 256 valeurs, de `00000000` (0) à `11111111` (255). C’est pourquoi chaque nombre d’une adresse IPv4 ne peut pas dépasser 255.

### Le tableau des valeurs de position

Chaque position dans un octet correspond à une puissance de 2. Il faut le connaître par cœur, car il sert dans les deux sens.

| Position | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|
| Puissance | 2⁷ | 2⁶ | 2⁵ | 2⁴ | 2³ | 2² | 2¹ | 2⁰ |
| Valeur | **128** | **64** | **32** | **16** | **8** | **4** | **2** | **1** |

Quand le bit vaut 1, on additionne sa valeur; quand il vaut 0, on ne l’ajoute pas.

| Bit | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 |
|---|---|---|---|---|---|---|---|---|
| Valeur | 128 | 64 | 0 | 0 | 0 | 0 | 0 | 0 |

Résultat : 128 + 64 = **192**, donc `11000000` = 192.

## 2. Décimal vers binaire

### Méthode 1 — Soustraction des valeurs de position

On prend le nombre décimal et on soustrait, de gauche à droite, la plus grande valeur possible du tableau. On écrit 1 quand on soustrait, 0 quand on ne peut pas.

**Exemple : convertir 192**

| Valeur | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|---|---|---|---|---|---|---|---|---|
| Peut-on soustraire? | oui | oui | non | non | non | non | non | non |
| Bit | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 |

- 192 − 128 = 64, il reste 64 → bit 1
- 64 − 64 = 0, il reste 0 → bit 1
- Les valeurs suivantes sont plus grandes que le reste, on écrit des 0.

Résultat : `11000000`

**Exemple : convertir 25**

- 25 est plus petit que 128, 64, 32 et 16 → quatre premiers bits à 0
- 25 − 16 = 9 → bit 1
- 9 − 8 = 1 → bit 1
- 1 − 4 impossible → 0
- 1 − 2 impossible → 0
- 1 − 1 = 0 → bit 1

Résultat : `00011001`

**Exemple complet : convertir 192.168.1.25**

| Octet | Calcul | Binaire |
|---|---|---|
| 192 | 128 + 64 | `11000000` |
| 168 | 128 + 32 + 8 | `10101000` |
| 1 | 1 | `00000001` |
| 25 | 16 + 8 + 1 | `00011001` |

```text
192.168.1.25 → 11000000.10101000.00000001.00011001
```

### Méthode 2 — Divisions successives par 2

On divise le nombre par 2 jusqu’à obtenir 0, on note chaque reste, puis on lit les restes **de bas en haut**.

**Exemple : convertir 25**

| Division | Quotient | Reste |
|---|---|---|
| 25 ÷ 2 | 12 | **1** |
| 12 ÷ 2 | 6 | **0** |
| 6 ÷ 2 | 3 | **0** |
| 3 ÷ 2 | 1 | **1** |
| 1 ÷ 2 | 0 | **1** |

On relit les restes du dernier au premier : `11001`. On complète à gauche avec des zéros pour obtenir 8 bits : `00011001`.

**Vérification de 168**

| Division | Quotient | Reste |
|---|---|---|
| 168 ÷ 2 | 84 | 0 |
| 84 ÷ 2 | 42 | 0 |
| 42 ÷ 2 | 21 | 0 |
| 21 ÷ 2 | 10 | 1 |
| 10 ÷ 2 | 5 | 0 |
| 5 ÷ 2 | 2 | 1 |
| 2 ÷ 2 | 1 | 0 |
| 1 ÷ 2 | 0 | 1 |

Restes lus du bas vers le haut : `10101000`, soit 168.

### Quelle méthode choisir?

- La **soustraction** est plus rapide quand on connaît le tableau des puissances de 2, car on travaille sur 8 positions seulement.
- Les **divisions** demandent plus d’étapes, mais elles fonctionnent avec n’importe quel nombre sans mémoriser de tableau.

## 3. Binaire vers décimal

### Méthode 1 — Addition des valeurs de position

On écrit les valeurs 128, 64, 32, 16, 8, 4, 2, 1 sous les 8 bits, puis on additionne uniquement les valeurs situées sous un 1.

**Exemple : `10101000`**

| Bit | 1 | 0 | 1 | 0 | 1 | 0 | 0 | 0 |
|---|---|---|---|---|---|---|---|---|
| Valeur | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

128 + 32 + 8 = **168**

**Exemple : `00011001`**

| Bit | 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 |
|---|---|---|---|---|---|---|---|---|
| Valeur | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

16 + 8 + 1 = **25**

**Exemple complet : `11000000.10101000.00000001.00011001`**

| Binaire | Addition | Décimal |
|---|---|---|
| 11000000 | 128 + 64 | 192 |
| 10101000 | 128 + 32 + 8 | 168 |
| 00000001 | 1 | 1 |
| 00011001 | 16 + 8 + 1 | 25 |

Résultat : **192.168.1.25**

### Méthode 2 — Le doublement progressif

On part de 0 et on parcourt les bits **de gauche à droite**. À chaque bit, on double le résultat courant et on ajoute le bit (0 ou 1).

Formule à répéter : `résultat = (résultat × 2) + bit`

**Exemple : `10101000`**

| Bit lu | Calcul | Résultat |
|---|---|---|
| 1 | (0 × 2) + 1 | 1 |
| 0 | (1 × 2) + 0 | 2 |
| 1 | (2 × 2) + 1 | 5 |
| 0 | (5 × 2) + 0 | 10 |
| 1 | (10 × 2) + 1 | 21 |
| 0 | (21 × 2) + 0 | 42 |
| 0 | (42 × 2) + 0 | 84 |
| 0 | (84 × 2) + 0 | 168 |

Résultat : **168**

**Exemple : `00011001`**

| Bit lu | Calcul | Résultat |
|---|---|---|
| 0 | (0 × 2) + 0 | 0 |
| 0 | (0 × 2) + 0 | 0 |
| 0 | (0 × 2) + 0 | 0 |
| 1 | (0 × 2) + 1 | 1 |
| 1 | (1 × 2) + 1 | 3 |
| 0 | (3 × 2) + 0 | 6 |
| 0 | (6 × 2) + 0 | 12 |
| 1 | (12 × 2) + 1 | 25 |

Résultat : **25**

Cette méthode est pratique pour vérifier un calcul rapidement, sans écrire le tableau complet.

## 4. Valeurs utiles à reconnaître

Certains octets reviennent souvent dans les masques de sous-réseau. Les reconnaître fait gagner du temps.

| Décimal | Binaire | Usage fréquent |
|---|---|---|
| 0 | `00000000` | réseau ou hôte non défini |
| 128 | `10000000` | moitié d’un octet |
| 192 | `11000000` | masque /26, début de plage privée 192.168.x.x |
| 224 | `11100000` | masque /27 |
| 240 | `11110000` | masque /28 |
| 248 | `11111000` | masque /29 |
| 252 | `11111100` | masque /30 |
| 254 | `11111110` | masque /31 |
| 255 | `11111111` | masque /32, diffusion locale |

On remarque que ces valeurs de masque sont toujours une suite de 1 suivie d’une suite de 0 : c’est la signature d’un masque de sous-réseau valide.

## 5. Erreurs fréquentes

- **Oublier les zéros à gauche** : `11001` doit s’écrire `00011001`. Sans les 8 bits, la position des bits change et la valeur devient fausse.
- **Dépasser 255** : un octet ne peut pas valoir 256 ou plus. Une adresse comme `192.168.300.1` est invalide.
- **Confondre bit et octet** : une adresse IPv4 a 32 bits, soit 4 octets, pas 8 bits.
- **Lire les restes dans le mauvais sens** : dans la méthode des divisions, on lit du bas vers le haut.
- **Sauter la vérification** : refaire le calcul dans l’autre sens permet de repérer une erreur immédiatement.

## 6. Vérifier avec un calculateur

Pour valider un exercice, on peut utiliser l’invite de commandes ou PowerShell sous Windows.

```powershell
# Décimal vers binaire (8 bits)
[Convert]::ToString(168, 2).PadLeft(8, '0')

# Binaire vers décimal
[Convert]::ToInt32('10101000', 2)
```

Résultats attendus : `10101000` et `168`.

## À retenir

- Un octet = 8 bits, avec les valeurs 128, 64, 32, 16, 8, 4, 2, 1.
- Décimal → binaire : soustraction des valeurs de position, ou divisions successives par 2 avec restes lus à l’envers.
- Binaire → décimal : addition des valeurs sous les 1, ou doublement progressif de gauche à droite.
- Une adresse IPv4 valide contient 4 octets, chacun entre 0 et 255, séparés par des points.

## Sources

- [RFC 791 — Internet Protocol](https://www.rfc-editor.org/rfc/rfc791)
- [Microsoft Learn — Adressage IPv4](https://learn.microsoft.com/fr-fr/troubleshoot/windows-client/networking/tcpip-addressing-and-subnetting)
- [Microsoft Learn — Convertir un nombre en binaire avec PowerShell](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.core/about/about_numeric_literals)
