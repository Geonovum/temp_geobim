# Handleiding Software

# Software

## Revit

*Begrippen*

*Internal Origin:* De oorsprong in Revit. Dit punt is niet te verplaatsen.

*Project Basepoint:* Lokaal Coördinatiepunt. Dit punt wordt gebruikt om modellen op elkaar af te stemmen b.v. tijdens engineering en/of wanneer Georeferentie niet relevant is.
*Survey Point:* CRS-Coördinatiepunt. CRS-Coördinatiepunt . Dit punt wordt gebruikt om de relatie te leggen met een coördinatenstelsel en zo de positie van het model op de aardbol vast te leggen.

*Project Units:* De instelling van de standaard eenheden binnen het project. Hier kan b.v. opgegeven worden of er met meters of met millimeters wordt gewerkt.
![Scherm in Revit dat Lokaal Coordinatiepunt en CRS-Coordinatiepunt laat zien](https://github.com/user-attachments/assets/7b10bf0a-77f0-456e-9ab1-e6840c05c3c5)


*Methode 1:* link DXF, DWG of RVT
1.	Gebruik een DXF, DWG of een RVT die op de juiste coördinaten is gemaakt als onderlegger en link die in Revit. (NB: het is handig om bij het linken op te geven dat het bestand in meters is). Gebruik bij voorkeur een onderlegger die gegeorefereerd is zodat Revit de EPSG-code overneemt en je die niet handmatig hoeft toe te voegen.
2.	Als er, zoals bij de start van een project, nog geen model is dan is het handig om in de onderlegger de positie van het CRS-Coördinatiepunt op te geven (kies een plek met hele X- en Y-waarden in het coördinatenstelsel).
3.	Verplaats en roteer de onderlegger naar een bekend punt of naar het model zodat de onderlegger op de juiste positie staat. Je verplaatst dus niet het model naar de juiste locatie maar je verplaatst de locatie naar het model.
4.	Gebruik ‘Aquire Coordinates’ en selecteer de onderlegger om de coördinaten over te nemen. (NB: “Save Position” van de DXF of DWG niet gebruiken, Revit maakt anders een Shared Coordinates bestand aan en wijzigt de locatie van de DXF of DWG waardoor die niet meer correct is.
5.	Selecteer het Survey Point, unclip het en verplaatst het naar de gekozen X- en Y-waarden van het CRS-Coördinatiepunt (hele X- en Y-waarden in het RD-stelsel) en geef als Z-waarde de hoogte ten opzichte van N.A.P. op. Clip vervolgens het Survey Point en verplaats het Survey Point in de Z-richting terug naar 0.
6.	Plaats een coördinatie-object op het Survey Point.
7.	Plaats een coördinatie-object op het Project Basepoint.
8.	Als het ontwerp zover is dat de stramienen vaststaan dan kan het Project Basepoint verplaatst worden zodat die op 5 of 10m van de eerste stramienen staat zoals gebruikelijk. Vóór het verplaatsten moet het Project Basepoint ge-unclipt worden. Verplaats vervolgens ook een coördinatie-object naar de nieuwe positie van het Project Basepoint.

*Methode 2: Project Basepoint en Survey Point aanpassen*
1.	Geeft het Revit bestand of een DWG-export uit het Revit bestand aan een landmeter of een BIM- of GIS-specialist en vraag om de RD-coördinaten van het Lokaal Coördinatiepunt (Project Basepoint) en vraag om een voorstel voor het CRS-Coördinatiepunt (Survey Point). 
2.	Zet in Revit de Project Units op meter.
3.	Unclip het Survey Point en verplaats het naar de opgegeven coördinaten van het Lokaal Coördinatiepunt (Project Basepoint). (NB: N/S=Y en E/W=X).
4.	Clip het Survey Point en verplaats het naar het Project Basepoint.
9.	Unclip het Survey Point en verplaats het naar de opgegeven coördinaten van het CRS-Coördinatiepunt (Survey Point) en geef als Z-waarde de hoogte ten opzichte van N.A.P. op. Clip vervolgens het Survey Point en verplaats het Survey Point in de Z-richting terug naar 0.
5.	Selecteer het Project Basepoint en geef de hoekverdraaiing ten opzichte van Grid-noord (True North) op. Het gaat hier om de hoekverdraaiing van Project North naar True North waarbij positief = tegen de klok in en negatief is met de klok mee. Revit zal negatieve hoekverdraaiingen omrekenen naar een positieve hoekverdraaiing.
6.	Zet eventueel de Project Units terug naar millimeter.

 *Controle*
 Het venster "Location and Site" geeft aan of alles goed is gegaan.
 <img width="1065" height="820" alt="image" src="https://github.com/user-attachments/assets/d229c509-434e-44a2-b7f9-9018d430ecde" />

*Units*
Door een omissie in de IFC-exporter van Revit moet voorafgaand aan het exporteren naar IFC de Project Units Length op meter ingesteld worden.

*Export naar IFC*
1.	Lokaal Coördinatiepunt: exporteer een IFC (4 of hoger) met Project Basepoint als Coordinate Base. De IFC is niet ge-Georefereerd (alleen de coordinaten van Project Basepoint zijn correct) en niet Grid-noord gericht (Project North in Revit).
![Scherm in Revit met instellingen voor IFC export met Project Basepoint als Coordinate Base](https://github.com/user-attachments/assets/c4bf15c6-3218-4455-8e02-82bab44b21c1)
2.	CRS-Coördinatiepunt: exporteer een IFC (4 of hoger) met Survey Point als Coordinate Base. Vul bij EPSG Code in: 28992. De IFC is ge-Georefereerd en is Grid-noord gericht (True North in Revit)

![Scherm in Revit met instellingen voor IFC export met Survey Point als Coordinate Base](https://github.com/user-attachments/assets/1c77bf8d-8c8b-4c37-bb9a-3a405c6dd5d1)


## ArchiCAD
--- 

## VectorWorks
--- 

## BricsCAD
--- 

## Sketchup
--- 

## Bonsai (BlenderBIM)
--- 

## Illustrator
--- 



## Definities
<dfn>Definitie</dfn>: Een definitie is een beschrijving van een woord. Een ander woord voor _definitie_ is betekenis of beschrijving.

