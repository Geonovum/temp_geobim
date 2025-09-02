# Coördinaatreferentiesystemen (GIS/GEO)

*todo, [Hoofdstuk 1.2](https://docs.geostandaarden.nl/crs/crs/) hier kopieren/samevatten*

# Lokale Coordinaten Systemen (BIM)

In BIM wordt altijd in een XYZ coordinatenstelsel gewerkt. Afhankelijk van het project wordt bepaald waar de oorsprong van het XYZ stelsel ligt. Er wordt meestal een oorsprong gekozen relatief dicht bij het te bouwen object. Dit is wenselijk voor het toepassen van 3D modeleer software.

# BIM naar GIS/GEO

Zoals hierboven beschreven komt de werkwijze van een geprojecteerd CRS overeen met de werkwijze in BIM. Beide maken gebruik van het XYZ Stelsel. Door een link te maken tussen het lokale coordinaten stelsel in BIM en een geprojecteerd CRS kan een BIM model verder gebruikt worden in GEO/GIS systemen met zo min mogelijk verlies van data. Vanaf hier kan GIS/GEO software gebruik maken van projecties en andere GIS tools om het BIM model te projecteren in de wereld en hier aanvullende analyse op te doen.

Hierbij moet wel aandacht besteed worden aan de onderstaande punten
- De oorsprong van het BIM coordinatenstels moet dicht bij de geometrie liggen zodat gridcorrecties beperkte inmpact hebben
- Er treed een onnauwkeurigheid op van ??mm per m tussen de oorsprong en het verste punt in het model *TODO, is dit waar?*

In sommige software pakketen zoals AutoCAD is het gebruikelijk wel op RD-coordinaten te werken. AutoCAD is alleen zelf niet bewust dat dit RD-coordinaten zijn. Wat de software betreft is dit een lokaal stesel zonder verdere betekenis. De link tussen de lokale coorditen en het geprojecteerd CRS is in dit geval X~bim~ = X~gis~, Y~bim~ = Y~gis~, Z~bim~ = Z~gis~

# GIS/GEO naar BIM

De meeste BIM software is niet instaat translaties uit te voeren tussen verschillende geprojecteerde CRS'en. Wanneer GIS data dus naar BIM moet worden uitgewisseld is het belangrijk dat dit al geprojecteerd is in het coordinatensysteem wat de BIM Software verwacht. Afhankelijk van de BIM Software kan het zelf nodig zijn te transleren naar het lokale stelsel wat gebruikt wordt door de BIM Software. Hier dienen duidelijk afspraken over gemaakt worden.


## Coördinaattransformatie, datumtransformatie en coördinaatconversie

Bij het gebruik van meerdere CRS-en bestaat risico op introductie van fouten door onjuiste implementatie van de relaties tussen CRS-en. Eindgebruikers worden geadviseerd data waar mogelijk op te vragen in hetzelfde CRS.

Aanbieders van data worden geadviseerd om data aan te bieden in de verschillende CRS-en gericht op de eindgebruikers. Hierbij is het advies zo nauwkeurig mogelijk te transformeren, omdat het niet altijd duidelijk is wie de eindgebruiker is.

Wanneer voor opslag, uitwisseling en/of visualisatie andere CRS-en worden gebruikt zijn er een aantal aandachtspunten, de belangrijkste zijn:

Voorkom dat te grote geometrische of topologische verschillen ontstaan
Maak gebruik van een eenduidige coördinaatransformatie (en leg dit vast)

bron: https://docs.geostandaarden.nl/crs/crs/
