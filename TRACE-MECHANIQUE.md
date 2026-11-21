# 📐 TRACE — Dossier de mécanique de jeu

Système de gameplay créé sur *Serpent Duels*, conçu pour être réutilisé dans d'autres jeux.
Toute mécanique listée ici porte un nom officiel : utilisez ces termes dans les règles,
l'UI et les futurs jeux.

## TRACE = le genre

> **T**raçage à main levée · **R**ythme au tour par tour · **A**nticipation dessinée ·
> **C**onfrontation simultanée · **É**volution par éclats

Reconnaissances d'un jeu TRACE :
1. les joueurs **dessinent** leurs déplacements (souris/doigt),
2. les plans sont exécutés **en simultané** après validation de tous les camps,
3. la capacité de déplacement dépend d'un **budget incarné par l'avatar**,
4. des **Éclats** sur la carte modifient les capacités entre deux tours.

## Le déplacement : la Corportée

La **Corportée** est la règle de déplacement fondamentale : la portée de déplacement
d'une entité est égale à sa longueur corporelle.

- grandir = gagner de la portée,
- se faire couper = perdre de la portée,
- le budget se « dépense » au fil du tracé.

## Vocabulaire officiel

| Terme | Définition |
|---|---|
| **Phase d'Encre** | Phase de planification : tracés dessinés à main levée, un camp après l'autre (écran partagé) ou contre l'IA |
| **Anneau-Jauge** | Cercle virtuel centré sur le bout du tracé ; son rayon représente la Corportée restante et rétrécit au fur et à mesure |
| **La Ruée** | Phase de résolution : tous les tracés sont exécutés en simultané |
| **Morsure** | Une tête qui traverse un corps adverse : le corps est coupé à ce point, la partie arrière est perdue |
| **Seuil de vitalité** | Longueur minimale ; en dessous, l'entité périt d'une morsure (serpent trop court) |
| **Éclats** | Pastilles de pouvoir sur la carte, ramassées au contact (croissance, vitesse, dash, feu, scission, hydre) |
| **L'Hydre** | Forme bicéphale : corps + 2 cous égaux pointant vers l'avant (règle : scission du corps en 2 moitiés égales, surplus impair au corps, minimum 3 segments de corps pour s'assimiler) |
| **Scission** | Éclat divisant une entité en deux entités plus petites, toutes deux contrôlées |
| **Dash** | Charge stockée, activable pendant la Phase d'Encre, consommée pour traverser une première collision |
| **Boréal** | (à définir) nom réservé pour un futur terrain ou mode |

## Réglages actuels (Serpent Duels)

| Constante | Valeur | Signification |
|---|---|---|
| `SEG` | 0.7 | Longueur d'un segment (unité de Corportée) |
| `BASE_SPEED` | 14 | Vitesse de Ruée (unités/s) |
| `ARENA_R` | 45 | Rayon de l'arène |
| `INIT_LEN` | 24 | Longueur initiale en segments |
| `PILL_START / PILL_MAX / PILL_EVERY` | 6 / 12 / 3.5s | Densité d'Éclats |
| Seuil de vitalité | 4 (ou 6 en Hydre) | Segments restants minimum |

## IA par paliers (référence pour futurs jeux)

- **Facile** : analyse le joueur, fuit, ne collecte pas — joue pour perdre
- **Moyenne** : collecte maximale + attaques d'opportunité
- **Difficile** : simule les deux mouvements dans le temps, intercepte la trajectoire future, sinon se met en parade défensive ; arme son dash si coincée
