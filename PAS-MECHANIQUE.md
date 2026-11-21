# 📐 PAS — Dossier de mécanique de jeu

Système de gameplay créé sur *Serpent Duels*, réutilisable dans d'autres jeux.
Deux noms officiels uniquement : **PAS** (le gameplay) et **sillage** (le déplacement).

## PAS : le gameplay

Un jeu « PAS » (un pas à la fois, au tour par tour) se joue ainsi :
1. les joueurs **dessinent** leurs déplacements (souris/doigt),
2. les plans sont exécutés **en simultané** après validation de tous les camps,
3. la capacité de déplacement dépend du **sillage** de l'avatar,
4. des pastilles de pouvoir sur la carte modifient les capacités entre deux tours.

## Sillage : le déplacement

Le **sillage** est la règle de déplacement fondamentale : la portée de déplacement
d'une entité est égale à sa longueur corporelle — elle laisse derrière elle un sillage,
et c'est ce sillage qui mesure ce qu'elle peut encore parcourir.

- grandir = gagner de sillage (aller plus loin au tour suivant),
- se faire couper = perdre du sillage,
- le budget se « dépense » au fil du tracé, quand le sillage s'assèche.

## Règles courantes (sans nom spécial)

- Planification au tour par tour, résolution simultanée
- Morsure : une tête qui traverse un corps le coupe à ce point ; la partie arrière est perdue
- Il existe une longueur minimale en dessous de laquelle l'entité périt
- Pastilles : croissance, vitesse, dash (stocké, activé à la planification),
  feu instantané, scission en deux entités, forme bicéphale (corps + 2 cous égaux vers l'avant)

## Réglages actuels (Serpent Duels)

| Constante | Valeur | Signification |
|---|---|---|
| `SEG` | 0.7 | Longueur d'un segment (unité de sillage) |
| `BASE_SPEED` | 14 | Vitesse de résolution (unités/s) |
| `ARENA_R` | 45 | Rayon de l'arène |
| `INIT_LEN` | 24 | Longueur initiale en segments |
| `PILL_START / PILL_MAX / PILL_EVERY` | 6 / 12 / 3.5s | Densité de pastilles |
| Longueur minimale | 4 (ou 6 en bicéphale) | Segments restants minimum |

## IA par paliers (référence pour futurs jeux)

- **Facile** : analyse le joueur, fuit, ne collecte pas — joue pour perdre
- **Moyenne** : collecte maximale + attaques d'opportunité
- **Difficile** : simule les deux mouvements dans le temps, intercepte la trajectoire future, sinon se met en parade défensive ; arme son dash si coincée
