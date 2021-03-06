# (cfv3-43) Ajustements à apporter aux templates des pages Séance

17 mai 2016

La page http://cinemathequefr.github.io/cfv3-43/ montre l'apparence voulue d'une page Séance. Cet exemple inclut des données provenant de tous les champs possibles.

Actuellement, une page Séance affiche moins d'informations sur les items (films / interventions) qui la constituent que les pages Film ou Intervention correspondantes.

Les informations manquantes sont principalement :

* Commentaire sur le film (= texte)
* Indication d'âge

Par exemple, on trouve sur  http://www.cinematheque.fr/film/100519.html un texte de présentation du film <em>Black Book</em> qui n'est pas présent sur la page Séance http://www.cinematheque.fr/seance/24608.html.

Le template actuel est également insatisfaisant pour ce qui concerne les espacements verticaux, qui ne rendent pas bien lisibles les différents blocs (p ex http://www.cinematheque.fr/seance/22799.html).

## Maquette de page Séance modifiée

###  Titre des cycles auxquels la séance est rattachée

> Rétrospective John Ford - Jeune public

* Quand il y a en plusieurs, ils sont affichés sur la même ligne, séparés par un tiret (\&dash;)
* Les liens sont soulignés à l'état hover/active

### Heures de début et fin, durée

L'affichage actuel est correct, mais il arrive que cette durée ne soit pas saisie dans le back.

* En cas de durée non saisie (ou égale à 0), afficher seulement l'heure de début (Ce problème se manifeste également ailleurs, à vérifier ultérieurement.)

### Bloc Titre + description de la manifestation (éventuel)

La présence d'un titre de manifestation et/ou d'une description de la manifestation génère un bloc.

* Ce bloc, quand il existe, est suivi d'un filet `hr.short`

#### Titre

> Programme 1 : Esthétique du western

* Pour des questions lisibilité, on retire les guillemets CSS qui encadrent actuellement le titre de la manifestation (p ex sur http://www.cinematheque.fr/seance/24675.html).  
*Cette modification ne concerne pas seulement la page Séance mais tous les emplacement sur le site, elle pourra être faite ultérieurement.*

#### Description

> En 1955, <em>La Prisonnière du désert</em> de John Ford (...)

OK, pas de changement.

### Blocs d'items (film / intervention)

* Entre les blocs d'items, on ajoute un séparateur `hr.short`

### Adaptation

> D'après Alan Le May.

* On ajoute le champ adaptation, non présent actuellement.  
*Attention : les données saisies sont parfois dans un élément `p` qui se retouve importé dans le gabarit. Il faut styler en conséquence pour supprimer cette marge de paragraphe non voulue.*

### Texte

> La Prisonnière du désert est un western majeur (...)

* On ajoute ce champ texte. A la différence de la page Film, on lui donne ici un corps de texte plus petit (14px). Dans cette zone, les paragraphes sont à séparer verticalement par 10px.

### Indication d'âge

> À partir de 9 ans

* On ajoute l'indication d'âge, non présente actuellement.  
*Attention : il faut mettre un accent grave : **À** au lieu de **A** (corriger aussi sur la page Film)*

### Bloc Intervention : durée

L'indication de durée est actuellement de la forme :

> Durée: 60 min

* Supprimer le label **Durée:**. On affiche directement la durée (comme pour les films).

### Bloc Intervention : remarque sur l'intervention

> Traduction simultanée en anglais

Correspond aux champs Remarque de chaque item sur le détail d'une séance. Ce champ est rarement utilisé pour une intervention, mais il faut le prévoir. Actuellement, cette donnée ne remonte pas sur la page Séance.

* Si une remarque est saisie sur cette intervention pour cette séance, on l'affiche après la durée, en séparant avec un slash.

### Bloc Intervention : biographie des intervenants

Actuellement, la biographie des intervenants n'est pas affichée.

* Afficher la biographie des intervenants avec le même style que les textes de présentation d'un film (14px).
* Séparer chaque intervention d'une marge verticale (10px) correspondant à la moitié de la marge standard de séparation des éléments.

---

## Autres remarques

* Il y a actuellement un bug dans le blocs film (p ex http://www.cinematheque.fr/seance/22689.html) : entre la ligne interprétation ("Avec Jean Gabin...") et le synopsis, une balise `<br>` créé un espacement vertical non voulu.
* Sur la maquette, les espacement verticaux entre les éléments sont normés. La marge verticale est de 20px et à 3 emplacement , on utilise la moitié de cette valeur :
  * Entre les titres de cycle et le titre de la séance (date/heure)
  * Entre la salle et la ligne heure de début / heure de fin / durée
  * Pour chaque item Intervention, entre les bios des intervenants







