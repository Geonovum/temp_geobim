# Methodes van Georeferentie

Er zijn verschillende methodes beschikbaar om een BIM en GEO modellen bij elkaar te brengen op de kaart. Deze methoden verschillen in nauwkeurigheid en mogelijkheid voor het bijeenbrengen van modellen. Dit wordt door Clemen Christian beschreven als Levels van georefereren [[Christian2019]].

Het is mogelijk om een BIM-model op de kaart te zetten door alleen het adres van waar het BIM-model dient te komen te duiden. Deze informatie geeft een indicatie van waar het model moet komen. De informatie is niet toereikend om het model exact te plaatsen, roteren en schalen. Een andere methode zoals het model plaatsen in een officieel coordinatenstelsel is hiervoor wel geschikt. Afhankelijk van de behoefte zijn verschillende methodes geschikt.

![Verschillende opties van georefereren schematisch weergegeven](media/georefereren_opties.png "Verschillende opties van georefereren schematisch weergegeven")

De beschikbaarheid van informatie voor het berekenen van georeferentie-parameteres voor de verschillende methoden is onderzocht door de TU Delft [[Hakim2024]]. Deze methodes, gefocused op gebouwen, kunnen worden opgeschaalt naar infrastructuur projecten. Zodoende kunnen de voorbeelden van Figuur YY, vertaald worden naar de volgende 3 onderdelen: (1) Gebruik van survey points, (2) Footprint alignment en (3) scan-to-BIM. Om deze methodes te kunnen toepassen legt dit hoofdstuk uit, welke datasets, kwaliteitsparameters en toepassingen nodig zijn om een BIM te kunnen georefrenen. 

## Geo datasets voor het referen van modellen in Infrastructuur
Voor het refrenen van datasets naar een geo domein, zijn de volgend datasets beschikbaar, die zijn weergegeven in Tabel YY. Hier is de bestandsnaam, eigenaar, nauwkeuigheid, dimiensie en locatie weergegeven. 

**Tabel YY.** Overzicht van nationale datasets beschikbaar voor geo-referentie van project data of modelen
| Naam             | Eigenaar            | Nauwkeurigheid        | Dimensie | Locatie / Dekking            |
| ---------------- | ------------------- | ---------------------- | -------- | ---------------------------- |
| **DTB / 1GiS / BGT** | Rijkswaterstaat | cm-nauwkeurig op objectniveau | 2.5D       | Landelijk, beheerde water/wegen-infrastructuur |
| **BGT**          | Kadaster | cm-nauwkeurig op objectniveau | 2D       | Landelijk|
| **AHN**          | Het Waterschapshuis | 5–10 cm (verticaal)   | 3D       | Landelijk               |
| **PMG**          | Rijkswaterstaat       | ± 2 cm (relatief)     | 3D       | RWS-wegennet, selectieve locaties |
| **NWB**          | Het Nationaalwegenbestand        | ± 1 m (topologisch)   | 2D       | Landelijk, wegennet (NL)     |
| **SpoorInBeeld** | ProRail    | ± 2 cm (relatief)     | 3D       | Spoortracés Nederland        |
| **Beeldmateriaal** | Het Waterschapshuis | ± 5–10 cm (projectie) | 2.5D     | Landelijk / stedelijk        |
| **NAP-netwerk**  | Kadaster / Rijkswaterstaat      | < 1 cm (verticaal)    | 1D (Z)   | Landelijk meetnet (peilmerken) |
| **BAG**          | Kadaster            | ± 10 cm (objectpositie) | 2D/2.5D  | Landelijk (NL)               |


Naast deze primaire geo datasets, kunnen geementes, provicies en centrale overheden andere datasets beschikbaar hebben, die kleiner van scope zijn. Ook zijn er datasets die zijn gextraheerd uit de bovenbenoemde datasets. Een voorbeeld is de 3DBAG, waar het AHN de basis is voor het maken van de deze dataset. Een analyse is in de verschillende hoogtedatasets in Nederland [source] en vanuit europa zijn de volgende hoogte datasets beschikbaar, die terug te vinden zijn via de volgende link. [https://3d.bk.tudelft.nl/europeantopography]


## Kwaliteits kenmerken voor geobestanden naar bim
De verschillende datasets die gebruikt kunnen worden, zijn van elkaar te onderscheiden. Het planimetrische en hoogtecomponent in een geo-databestand vormt een fundamenteel onderdeel van de dataset. Afwijkingen in deze informatie, of verschillen tussen diverse momenten van inwinning of ontwerp, kunnen een grote impact hebben. Het correct refereren van het bestand ten opzichte van deze assen is daarom essentieel om de juiste stappen te kunnen nemen.

Het doel van het refereren van een model binnen het geo-domein is het positioneren ervan in de echte wereld. Deze echte wereld bestaat uit een lokaal en een globaal coördinatensysteem. Zoals eerder beschreven, wordt een BIM-model in de toegepaste softwarepakketten vaak in een 0,0,0-referentiesysteem geplaatst. Daarentegen bevatten globale coördinaten aanzienlijk grotere waarden, wat ertoe kan leiden dat een dataset vastloopt binnen een applicatie. De documentatie van het gebruikte coördinatensysteem is eveneens van cruciaal belang. Wanneer dit systeem niet correct is vastgelegd, kunnen er problemen ontstaan tijdens de conversie van de hoogtecomponent. De meest gebruikte coördinatenstelsels in Nederland zijn weergegeven in Tabel YY. 

**Tabel YY.** Overzicht van de globale coordinatensystemen gebruikt in Nederland
| Naam      | Orientatie | EPSG      | Toelichting                                                                                                                                                              |
| --------- | ---------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **RDNAP** | XYZ        | **7415**  | Dit is een *compound coordinate reference system* (CRS) dat RD (XY, EPSG:28992) combineert met NAP (Z, EPSG:5709). Dus: X=Easting (RD), Y=Northing (RD), Z=hoogte (NAP). |
| **RD**    | XY         | **28992** | Planimetrisch systeem (Rijksdriehoeksstelsel) — X is oost, Y is noord.                                                                                                   |
| **NAP**   | Z          | **5709**  | Verticaal referentiesysteem, hoogte in meters t.o.v. Normaal Amsterdams Peil.                                                                                            |

*Voor meer informatie naar het gebruik van coordinaterefrentie systemen, zie de handreiking: https://docs.geostandaarden.nl/crs/crs/ *

### Primaire kwaliteits kenmerken voor geobestanden naar bim
Voor het gebruik van een dataset uit het **GIS-domein** zijn verschillende kenmerken van belang voor de toepassing binnen een **BIM-systeem**. Niet alle data is even geschikt om gebruikt te worden, naast het gerbuik van het juiste coordinaten systeem, spelen er kwailiteits kenmerken mee die van invloed zijn op zowel de ingewonnen als de gerbruikte referenetie data. Op basis van de onderzoeken en initiatieven  
*[Bron: IHN / Geonovum / DigiGo]* kunnen de volgende componenten worden meegenomen, let wel er zijn meer componenten die van invloed zijn op de kwaliteit en bruikbarheid van de data. 

### 1. Geografische distributie van de meet punten
Afhankelijk van de inwin methode, is de geografische distributie van de meetpunten van belang. Dit heeft namelijk een direct effect van het onderscheiden van objecten in het terrein, maar ondersteunt ook in correct vinden van de refrenetie punten. De distributie wordt omschreven door de hoeveelheid punten per vierkante meter of door de minimale afstand tussen de punten. De leert praktijk is een hoge puntdichtheid gekoppeld aan een hoger detailniveau van het 3D-model.

### 2. De absolute en relatieve nauwkeurigheid van een geo-dataset
In de literatuur en uitvraag­specificaties wordt een onderscheid gemaakt tussen de **absolute** en **relatieve** nauwkeurigheid van een geo-dataset. De **absolute nauwkeurigheid** beschrijft de afwijking tussen de inwinning of het model en de werkelijkheid, terwijl de **relatieve nauwkeurigheid** vaak wordt gebruikt om de afwijking tussen meetpunten binnen overlappende inwinningen te omschrijven. Een voorbeeld hiervan is een dwarsprofiel over een ingewonnen stuk snelweg. Beide typen nauwkeurigheden worden uitgedrukt in een planimetrische (XY) en een altimetrische (Z) component. De verschillende uitvraag­specificaties laten zien dat de relatieve nauwkeurigheid altijd kleiner is dan de absolute nauwkeurigheid.

### 3. De classificatieparameters in een geo-dataset
De wijze waarop objecten binnen een geo-dataset worden geclassificeerd, is essentieel voor de bruikbaarheid binnen een BIM-context. De toegepaste classificatiemethode vormt een belangrijke kwaliteitsparameter, bijvoorbeeld wanneer classificatie wordt uitgevoerd door kunstmatige intelligentie (AI) of door menselijke experts. Daarnaast zijn de gebruikte definities een cruciaal startpunt binnen dit proces. Zo kan de classificatie van vegetatie in de referentiedataset niet automatisch dezelfde definitie hebben als in de ingewonnen dataset, wat kan leiden tot interpretatieverschillen of inconsistenties in het uiteindelijke model.

### 4. De inwindatum van de geo-dataset
Het moment van inwinning bepaalt de bruikbaarheid van de dataset, aangezien iedere geo-dataset die wordt weergegeven in een GIS-omgeving een momentopname is. Een geo-dataset vertegenwoordigt nooit de volledige werkelijkheid, maar vormt slechts een benadering van de omgeving. Hierdoor kan de omgeving, afhankelijk van de mate van verandering, in de loop van de tijd sterk of minder sterk afwijken van de oorspronkelijke weergave. Dit wordt geïllustreerd in de onderstaande figuren aan de hand van de stationsregio van Delft, zoals weergegeven in het Actueel Hoogtebestand Nederland en de 3D Basisvoorziening, waarbij de bouw van de stationsregio een ingrijpende verandering in het terrein laat zien.

![Leefttijd van verschillende puntenwolken van de stations regio in Delft](media/Regio_delft_verandering.png "Verschillende opties van georefereren schematisch weergegeven")

## Georeferentie toepassingen voor BIM naar Geo

Om een model te georefereren, zijn er drie mogelijkheden om dit toe te passen: (1) Gebruik van survey points, (2) Footprint alignment en (3) scan-to-BIM gebaseerd op [BuildingSMART et al. (2020)]  [HAKIM]. Voor iedere methode van georeferentie wordt in de theorie nader toegelicht hoe deze kan worden toegepast. Let wel, bij de derde mogelijkheid is het model reeds gerefereerd, en is er in de meeste gevallen een conversiebestand beschikbaar dat het model vertaalt van een BIM-softwareomgeving naar het coördinatensysteem waarin de puntenwolk is ingewonnen.

Daarom wordt geadviseerd om uitsluitend bij optie 1 en 2 een beoordelingstoets uit te voeren, om te verifiëren of het model zich daadwerkelijk op de correcte locatie bevindt

### Het gebruik van survey points
Voor kleine netwerken worden vaste meetpunten op plekken waarvan met een bepaalde zekerheid gezegd kan worden dat deze niet verstoord of weg kunnen gaan. De meetpunten worden in XYZ bepaald, en kunnen beschouwd worden als stabiel in het terrein. De bepaling in XY wordt door middel van GNSS uitgevoerd met een nauwkeurigheid van 2-3cm. Er kan gekozen worden om de meetpunten direct via GNSS te bepalen indien dit mogelijk is. Wanneer dit niet mogelijk is, bv als de meetpunten in de muur/wand zitten, worden er tijdelijke punten gemaakt en via tachymetrie de XY bekend gemaakt. Door middel van waterpassing wordt de hoogte (Z) in mm nauwkeurigheid bepaald.

Bij het verwerken van lange netwerken kan er gekozen worden voor referentievelden, deze wordt op dezelfde manier bepaald, maar alleen via GNSS aan elkaar gekoppeld in XY. Voor de hoogte kan een waterpassing uitgevoerd worden per veld. Het geodetisch netwerk wordt gebruikt om een puntenwolk te geo-refereren, hiervan wordt een BIM model gemaakt. Er kan een controle uitgevoerd worden door de coördinaten en het BIM model te vergelijken.

### Footprint alignment
Voor de footprint alignment moet rekening worden gehouden met zowel het planimetrische als het altimetrische component. Om het ongerefereerde model naar een gerefereerde omgeving te brengen op basis van de footprint, dient een iteratief proces te worden opgezet. Dit proces start met een grove schatting van het planimetrische component, waarna aan de hand van patroonherkenning het hoogtecomponent verder wordt gerefereerd. Om dit te kunnen uitvoeren binnen Infrastructuur projecten, kunnen de volgende 2 objecten gebruikt worden: (1) noklijnen en (2) straatmeubilair. 

*Noklijnen*
Als de planimetrische componenten van de dataset op juiste plek liggen, is het nog steeds van belang om het hoogte component op de juiste manier te referen. Vanuit het IHN-project is gebleken dat er in Nederland belangrijke methoden beschikbaar zijn om data die niet zijn gerefereerd of die geen 3D-informatie bevatten, te koppelen aan bestaande referentiesystemen. Hiervoor kan bijvoorbeeld gebruik worden gemaakt van noklijnen die zijn geëxtraheerd uit het Actueel Hoogtebestand Nederland (AHN). [source: https://www.ahn.nl/integrale-hoogtevoorziening-nederland]
Deze methode, vrij beschikbaar via de dataroom van het AHN, maakt het mogelijk om de beschikbare noklijnen binnen het projectgebied te gebruiken als referentie voor het positioneren van het model ten opzichte van de GIS-laag. Een aandachtspunt is echter dat deze datasets beschikbaar zijn in GPKG-formaat, waardoor de gebruiker de data handmatig moet converteren naar een DWG-bestand om deze binnen gangbare BIM-software te kunnen gebruiken.

*Straatmeubilair*
Omdat een ingewonnen weg vaak geen woningen bevat, is het gebruik van noklijnen beperkt voor de hoogteregistratie in infrastructurele BIM-modellen buiten stedelijke gebieden. In dergelijke gevallen kan straatmeubilair worden gebruikt, zoals wegmarkeringen, kantverharding of objecten met een duidelijk herkenbare vorm.
Datasets die hierbij van cruciaal belang zijn, zijn het DTB (Digitaal Topografisch Bestand) en het AHN (Actueel Hoogtebestand Nederland). Deze datasets bevatten informatie in 2.5D, wat betekent dat er slechts één hoogtecomponent per coördinaat beschikbaar is. De waarde van dit hoogtecomponent varieert per objecttype. Daarom is het raadzaam om bij grote infrastructuurprojecten het handboek van het DTB te raadplegen. Er wordt onderscheid gemaakt van objecten met een hoge prioriteit en met lage. Dit kan een nauwkuerigheids verschil opleveren tussen de YY cm en ZZ cm. 
In de onderstaande figuur is een BIM-model weergegeven in combinatie met het DTB, waarbij de wegmarkeringen in dit geval goed op elkaar aansluiten. Deze overeenkomst kan worden gebruikt om het hoogtecomponent te realiseren, mits het planimetrische vlak reeds correct is vastgesteld.
Het AHN of een andere puntenwolk in de omgeving kan hiervoor eveneens worden gebruikt. Dit komt doordat de intensiteit, die de basis vormt van een puntenwolk, significant lager is op de weg dan op het omliggende meubilair. Daardoor is het vinden van deze objecten eenvoudiger en kunnen zij gemakkelijk uit de dataset worden geëxtraheerd.

# Georeferentie in uitwisseling
# IFC
- IfcPostalAddress
- IfcSite RefLatitude RefLongitude RefElevation
- IfcAxis2Placement3D
- IfcGeometricRepresentationContext
- IfcMapConversion 
- Het gebruik van generic property sets voor 

- IFC 5 (JSON?)
IFC 5 maakt gebruik van USD-formaat (Universal Scene Description), voor geometrie, bijvoorbeeld usdgeom::mesh – veelhoekig oppervlaktemodel.



calculated transformation parameters could may be stored -without extending IFC schema- through generic property sets

- IFC 5 (JSON?)
IFC 5 maakt gebruik van USD-formaat (Universal Scene Description), voor geometrie, bijvoorbeeld usdgeom::mesh – veelhoekig oppervlaktemodel.

# DXF
De objecten in de DXF worden getekend in een coördinatenruimte die matcht met een geprojecteerd CRS (zoals EPSG:28992 of EPSG:3857).

De coördinaten zijn dan in meters, zoals in GIS.

Voorbeeld: een lijn van (110000, 450000) naar (110500, 450500) is dan correct gepositioneerd in RD-coördinaten.

Maar: het DXF-bestand zelf bevat geen metadata die zegt: "dit is RD-coördinaten".

| Bestand	| Inhoud | 	Doel| 
| bestand.dxf	| De geometrie	| CAD-weergave| 
| bestand.prj	| CRS-informatie (in WKT)	| Georeferentie door GIS-software| 

# CityGML 

Individuele georeferentie:
<gml:Point srsName="urn:ogc:def:crs:EPSG::28992">
  <gml:pos>123456 456789</gml:pos>
</gml:Point>

Totaal georeferentie van model: 
<gml:boundedBy>
  <gml:Envelope srsName="urn:ogc:def:crs:EPSG::28992">
<gml:boundedBy>
=======

# Geopackage
Opslag van dit CRS in de tabel gpkg_spatial_ref_sys in het bestand

# API

Accessing Collections using HTTP GET returns a response that contains at least the list of collections. For each Collection, a link to the items in the collection (Features, path /collections/{collectionId}/items, link relation items) as well as key information about the collection. This information includes:

A local identifier for the collection that is unique for the dataset;

A list of coordinate reference systems (CRS) in which geometries may be returned by the server: the first CRS is the default coordinate reference system (in the Core, the default is always WGS 84 with axis order longitude/latitude);

▪ GET /collections/{collectionId}/items/{featureId}
  ▪ Opvragen individueel item
▪ GET /collections/buildings/items?crs={crsuri}
  ▪ Opvragen in specifiek CRS
  ▪ De default is CRS84
