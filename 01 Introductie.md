# Introductie
De integratie van Geo met BIM maakt het mogelijk om de interactie tussen bouwwerk en omgeving te modelleren en inzichtelijk te maken in diverse ontwikkelstadia en kan zo het ontwerp-, beheer-, ontwerp- en besluitvormingsproces versnellen. [[Mallela2024]]

De behoefte aan data delen tussen de Geo- en BIM-wereld lijkt vanzelfsprekend, omdat beide werelden op het niveau van een bouwwerk dezelfde objecten lijken te definiëren. Maar voor zinvolle integratie is het goed om te beseffen dat beide werelden een andere modelleer-benadering hebben en daarom ook verschillen kennen die overbrugd moeten worden. 

Een fundamenteel verschil is het gebruik van een lokaal coördinatenstelsel in BIM versus het gebruik van een geografisch coördinatenstelsel in Geo. Dit kan worden opgelost door BIM-modellen te georefereren, maar dat is in de praktijk nog niet triviaal. Je gaat immers van een cartesisch, orthogonaal coördinatenstelsel waarbij de afstand tussen twee coördinaatlijnen constant is over naar coördinaten die de vorming van de aarde representeren. Vooral voor bouwwerken en infrastructuur die een groot gebied omvatten kan dit een ongewenste vertekening geven. Momenteel is dit technisch op te lossen, maar het vraagt in de praktijk veel uitzoekwerk en is bovendien niet als standaard workflow beschikbaar binnen de mainstream software omgevingen. De uitdaging hier is het ontwikkelen van breed gedragen, gestandaardiseerde oplossingen met duidelijke handreikingen zodat deze oplossingen ook beschikbaar komen voor klein-tot-middelgrote projecten waar niet altijd de benodigde expertise beschikbaar is. [[Stoter2020]]

Deze praktijkrichtlijn is bedoeld voor GEO- en BIM-modelleurs van infra en utuliteitsbouw. De richtlijn voorziet in werkwijze en oplossingen die nodig zijn om Geo en BIM te georefereren. Het biedt een Informatie Levering Handleiding gebaseerd op open standaard uitwisseling. 

## Georeferentie in de B&U
*todo*

## Georeferentie in de Infra

### Kenmerken van Infraprojecten
Infraprojecten kenmerken zicht vaak door langgerekte projecten. De noodzaak en de positie van de objecten die gebouwt worden wordt bepaald door de omgeving. Het is vaak ook noodzakelijk om aan te sluiten op de bestaande omgeving. Als gevolg hiervan zijn er veel raakvlakken moet de omgeving. Om deze raakvlakken goed in kaart te brengen is het goed in kaart brengen van de omgeving zeer belangrijk. Om alle objecten in de omgeving te positioneren wordt gebruik gemaakt van RD-Coordinaten.

Voorbeelden van Infra projecten zijn 
 - snelwegen, tunnel, dijkverstrekingen (lang gerekt)
 - burgen, viaducten en sluizen (locatie bepaald door omgeving)

### Werkwijze in Infa
Binnen een project in de Infra denken we in RD coordinaten ten opzichten van NAP. Er wordt niet in een lokaal coordinaten stelsel gewerkt. Dit wordt 
gedaan omdat er vaak aagesloten moet worden op bestaande infrastructuur. Deze infrastructuur wordt door onze maatvoerder opgemeten in 
het RD-stelsel. Op basis hiervan kan verder worden ontworpen. Ook andere geometrische informatie welke benodigd is voor het project wordt
vaak in RD beschikbaar gesteld. Het RD-Stelsel is dus een logische afspraak om te gebruiken voor het ontwerp van een infraproject.

Het ontwerp wordt direct in het RD stelsel (een Geprojecteerd CRS) uitgewerkt, op tekeningen staan RD coordinaten en NAP niveau aangegeven om de locaties van (een deel van) een kustwerk aan te geven. Translate van het ontwerp in het RD-stelsel naar de werkelijkse situatie buiten wordt gedaan door maatvoerders. Zij vertalen (middels gespecialiseerde software en total stations) de RD coordinaten van het ontwerp naar een Geografische CRS zodat het in de werkelijke wereld geplaatst kan worden. Hierbij wordt gebruik gemaakt van grondslagen om de nauwkeurigheid tot op het gewenste niveau te krijgen.

### Toepassing van 3D Software
Tijdens het ontwerp proberen we onze ontwerpsoftware af te stellen op het feit dat we in RD coordinaten werken zodat dit overeenkomt met de manier
waarop wij denken binnen het project. Afhakelijk van de software wordt binnen de software nog steeds een lokaal stelsel gebruikt maar dit heeft geen waarde
voor het project team. In Revit wordt bijvoorbeeld nog steeds een Basepoint gebruikt maar de locatie hiervan is niet persee relevent voor
het project. Vaak wordt een mooi afgerond RD-coordinaat genomen. In andere software zoals AutoCAD of Civil3D wordt direct gewerkt op RD-coordinaten.
Er wordt in dit geval zeer ver van het orginele nulpunt getekend in de software.

Uitwisseling tussen verschillende software systemen gebeurd ook standaard op basis van RD-Coordinaten. Dit werkt echter niet fijnloos binnen het huidige softwarelandschap omdat de gebruikte software niet altijd op de hoogte is of in staat is te begrijpen dat er op RD-Coordinaten gewerkt wordt. De software interpeteerd de uitwisselbestanden bijvoorbeeld als bestanden met een lokaal coordinatenstelsel met zeer grote coordinaten in plaatst van RD-Coordinaten. Positionering gaat hierdoor niet altijd goed.