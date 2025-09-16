# Methodes van Georeferentie

Er zijn verschillende methodes beschikbaar om een BIM en GEO modellen bij elkaar te brengen op de kaart. Deze methoden verschillen in nauwkeurigheid en mogelijkheid voor het bijeenbrengen van modellen. Dit wordt door Clemen Christian beschreven als Levels van georefereren [[Christian2019]].

Het is mogelijk om een BIM-model op de kaart te zetten door alleen het adres van waar het BIM-model dient te komen te duiden. Deze informatie geeft een indicatie van waar het model moet komen. De informatie is niet toereikend om het model exact te plaatsen, roteren en schalen. Een andere methode zoals het model plaatsen in een officieel coordinatenstelsel is hiervoor wel geschikt. Afhankelijk van de behoefte zijn verschillende methodes geschikt.

![Verschillende opties van georefereren schematisch weergegeven](media/georefereren_opties.png "Verschillende opties van georefereren schematisch weergegeven")

De beschikbaarheid van informatie voor het berekenen van georeferentie-parameteres voor de verschillende methoden is onderzocht door de TU Delft. [[Hakim2024]] 

| Methode                                                   | Plaatsing     |  Rotatie      | Schaal        |
| -------------------------------------------------------   | ------------- | ------------- | ------------- |
| Benoemen van locatie                                      | Niet mogelijk | Niet mogelijk | Niet mogelijk | 
| Punt op de kaart zetten                                   | Mogelijk      | Niet mogelijk | Niet mogelijk |
| Locatie koppelen aan één element in het model             | Mogelijk      | Eventueel mogelijk | Niet mogelijk |
| Locatie koppelen aan geheel model en noorden aangeven     | Mogelijk      | Eventueel mogelijk | Niet mogelijk |
| Het model plaatsen in een officieel coördinatenstelsel    | Mogelijk      | Mogelijk              | Mogelijk |
| Het afspreken van controlepunten tussen BIM, Bouw en GEO  | Mogelijk      | Mogelijk | Mogelijk |

## 1D 2D en 3D Geo en BIM modellen

Zowel BIM- als GEO-modellen kunnen een 1D, 2D als 3D coordinatenstelsel gebruiken. Om een juiste  

Een GEO coordinatenstelsel kan 3D (EPSG:7415), 2D (EPSG:28992) of 1D (EPSG:5709) zijn. 

| Van           | Naar      |  Mogelijkheid | 
| -----------   | -------   | ------------- |
| 2D BIM        | 2D GEO    | ... | 
| 2D BIM        | 3D GEO    | ... | 
| 3D BIM        | 2D GEO    | ... | 
| 3D BIM        | 3D GEO    | ... | 

# Georeferentie in uitwisseling

# IFC
- IfcPostalAddress
- IfcSite RefLatitude RefLongitude RefElevation
- IfcAxis2Placement3D
- IfcGeometricRepresentationContext
- IfcMapConversion 
- Het gebruik van generic property sets voor 

calculated transformation parameters could may be stored -without extending IFC schema- through generic property sets

- IFC 5 (JSON?)
IFC 5 maakt gebruik van USD-formaat (Universal Scene Description), voor geometrie, bijvoorbeeld usdgeom::mesh – veelhoekig oppervlaktemodel.





IFC (Industry Foundation Classes) is een open en neutraal bestandsformaat dat wordt ontwikkeld en beheerd door buildingSMART International. Het is bedoeld om interoperabiliteit tussen verschillende softwareplatformen in de bouwsector mogelijk te maken, en is een kernonderdeel van openBIM. [Buildingsmart](https://ifc43-docs.standards.buildingsmart.org/IFC/RELEASE/IFC4x3/HTML/content/scope.htm).

In de meeste gevallen wordt een IFC bestand gemaakt middels een export uit een ander softwarepakket [^1]. Als gevolg hiervan is het de verantwoording van de leveringacier van het software pakket om de translatie te maken van de native bestanden naar een IFC bestand. Door verschillende implementatie in verschillende softwarepakketen is er een grote variatie ontstaat in IFC bestanden. Om hier meer consistentie in aan te brengen is Building Smart de [IFC Validation Service](https://www.buildingsmart.org/users/services/validation-service/) begonnen.

[^1]: Er bestaan wel software pakketen welke IFC bestanden direct kunnen maken en aanpassen maar deze zien beperkt gebruik in de industrie. 

## Georeferentie in IFC

In IFC wordt standaard gewerkt met een lokaal coordinaten stelsel. Dit wordt gedefineerd door een [IfcGeometricRepresentationContext](https://ifc43-docs.standards.buildingsmart.org/IFC/RELEASE/IFC4x3/HTML/lexical/IfcGeometricRepresentationContext.htm). Vanaf dit nulpunt wordt het 3D model opgebouwd. Hierbij wordt veelvoudige gebruik gemaakt van translaties middels een [IfcLocalPlacement](https://ifc43-docs.standards.buildingsmart.org/IFC/RELEASE/IFC4x3/HTML/lexical/IfcLocalPlacement.htm). Dit is een veel gebruikte methode in 3D software om coordinaten van geometrie klein te houden en geometrie op verschillende locaties te kunnen hergebruiken. (https://en.wikipedia.org/wiki/Local_coordinates)

Sinds IFC4 is het wel mogelijk om een referentie naar een geprojecteerd CRS te maken in een IFC bestand middels [IfcMapConversion](https://ifc43-docs.standards.buildingsmart.org/IFC/RELEASE/IFC4x3/HTML/lexical/IfcMapConversion.htm) en [IfcProjectedCRS](https://ifc43-docs.standards.buildingsmart.org/IFC/RELEASE/IFC4x3/HTML/lexical/IfcProjectedCRS.htm). Hiermee wordt het mogelijk om de relatie tussen het lokale nullpunt in het IFC bestand en een Geprojecteerd CRS vast te leggen in een IFC bestand. Dit wordt gedaan op basis van EPSG-codes. Het uitgangspunt is dat het importerende software pakket weer hoe met de EPSG-codes omgegaan moet worden. Er wordt geen aanvullende informatie gegeven over projecties. BIM software kan deze functionaliteit gebruik om translaties tussen IFC bestanden met de zelfde EPSG-codes correct te verwerkten. GIS software kan deze functionaliteit om geprojecteerd CRS om te zetten naar een Geografische CRS en het model te projecteren in de wereld.

# CityGML 

Individuele georeferentie:
<gml:Point srsName="urn:ogc:def:crs:EPSG::28992">
  <gml:pos>123456 456789</gml:pos>
</gml:Point>

Totaal georeferentie van model: 
<gml:boundedBy>
  <gml:Envelope srsName="urn:ogc:def:crs:EPSG::28992">
<gml:boundedBy>

# DXF
De objecten in de DXF worden getekend in een coördinatenruimte die matcht met een geprojecteerd CRS (zoals EPSG:28992 of EPSG:3857).

De coördinaten zijn dan in meters, zoals in GIS.

Voorbeeld: een lijn van (110000, 450000) naar (110500, 450500) is dan correct gepositioneerd in RD-coördinaten.

Maar: het DXF-bestand zelf bevat geen metadata die zegt: "dit is RD-coördinaten".

| Bestand	| Inhoud | 	Doel| 
| bestand.dxf	| De geometrie	| CAD-weergave| 
| bestand.prj	| CRS-informatie (in WKT)	| Georeferentie door GIS-software| 

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