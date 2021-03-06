# Ti.WFS
Client for  Web Feature Service (Open Geospatial) for Axway Titanium

<img src="http://www.opengeospatial.org/pub/www/files/OGC_Logo_2D_Blue_x_0_0.png" width=300 />
With this module you can use WFS services.

## Usage

```
var Wfs = require("ti.wfs").createWFS("https://geodienste.hamburg.de/HH_WFS_Strassenbaumkataster","2.0.0");

Wfs.getFeature({
   region : {
   	     latitude: 53.53,
   	     longitude: 10.0,
   	     latitudeDelta : 0.05,
   	     longitudeDelta: 0.05
   },
   typeNames : "app:Strassenbaumkataster"
}, function(e){
		 console.log(e.data)
});
```

And you will get:

```
{
  "wfs:FeatureCollection": {
    "-xmlns:xsi": "http://www.w3.org/2001/XMLSchema-instance",
    "-xmlns:wfs": "http://www.opengis.net/wfs/2.0",
    "-timeStamp": "2018-01-20T14:05:53Z",
    "-xmlns:gml": "http://www.opengis.net/gml/3.2",
    "-numberMatched": "unknown",
    "-numberReturned": "0",
    "wfs:member": [
      {
        "app:strassenbaumkataster": {
          "-xmlns:app": "http://www.deegree.org/app",
          "-gml:id": "APP_STRASSENBAUMKATASTER_2299",
          "app:baumid": "100374421",
          "app:gattung": "Tilia / Linde",
          "app:gattung_latein": "Tilia",
          "app:gattung_deutsch": "Linde",
          "app:art": "Tilia x europea / Kaiser-Linde",
          "app:art_latein": "Tilia x europea",
          "app:art_deutsch": "Kaiser-Linde",
          "app:sorte_latein": "Tilia x europea 'Pallida'",
          "app:sorte_deutsch": "Kaiser-Linde",
          "app:pflanzjahr": "2011",
          "app:kronendurchmesser": "2",
          "app:kronendmzahl": "2 m",
          "app:stammumfang": "20",
          "app:stammumfangzahl": "20 cm",
          "app:strasse": "Harburger Chaussee",
          "app:hausnummer": "g123",
          "app:stand_bearbeitung": "2017-01-01",
          "app:bezirk": "Hamburg-Mitte",
          "app:geom": {
            "gml:Point": {
              "-gml:id": "APP_STRASSENBAUMKATASTER_2299_APP_GEOM",
              "-srsName": "EPSG:25832",
              "gml:pos": "566545.620 5930635.407"
            }
          }
        }
      }]
    }  
}  
Wfs.getFeature(xml, function(e){
  console.log(e.data)
);
```

### Filtering etc.
If you want filter the request you have to use XML. In this case the first parameter is a xml string:

```
var xml = "<?xml version='1.0' encoding='UTF-8'?>
<wfs:GetFeature service="WFS" version="1.1.0" resultType="hits" xmlns:app="http://www.deegree.org/app" xmlns:wfs="http://www.opengis.net/wfs" xmlns:gml="http://www.opengis.net/gml" xmlns:ogc="http://www.opengis.net/ogc" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.opengis.net/wfs http://schemas.opengis.net/wfs/1.1.0/wfs.xsd">
    <wfs:Query typeName="app:strassenbaumkataster">
        <ogc:Filter>
            <ogc:And>
                <ogc:PropertyIsEqualTo>
                    <ogc:PropertyName>app:gattung</ogc:PropertyName>
                    <ogc:Literal>Taxus / Eibe</ogc:Literal>
                </ogc:PropertyIsEqualTo>
                <ogc:PropertyIsGreaterThanOrEqualTo>
                    <ogc:PropertyName>app:pflanzjahr</ogc:PropertyName>
                    <ogc:Literal>1920</ogc:Literal>
                </ogc:PropertyIsGreaterThanOrEqualTo>
                <ogc:PropertyIsLessThan>
                    <ogc:PropertyName>app:pflanzjahr</ogc:PropertyName>
                                       <ogc:Literal>0</ogc:Literal>
                </ogc:PropertyIsGreaterThanOrEqualTo>
                <ogc:PropertyIsLessThan>
                    <ogc:PropertyName>app:stammumfang</ogc:PropertyName>
                    <ogc:Literal>1001</ogc:Literal>
                </ogc:PropertyIsLessThan>
            </ogc:And>
        </ogc:Filter>
    </wfs:Query>
</wfs:GetFeature>";

Wfs.requestFeature(xml, function(e){
		 console.log(e.data)
);


```

## Other methods

### getCapabilities()
 	Generates a metadata document describing a WFS service provided by server as well as valid WFS operations and parameters
### describeFeatureType()
Returns a description of feature types supported by a WFS service

```
Wfs.describeFeatureType()
```
Gives you:

```
{
  "schema": {
    "-xmlns": "http://www.w3.org/2001/XMLSchema",
    "-xmlns:gml": "http://www.opengis.net/gml/3.2",
    "import": {
      "-namespace": "http://www.opengis.net/gml/3.2",
      "-schemaLocation": "http://schemas.opengis.net/gml/3.2.1/gml.xsd"
    },
    "element": [
      {
        "-name": "strassenbaumkataster",
        "-substitutionGroup": "gml:AbstractFeature",
        "complexType": {
          "complexContent": {
            "extension": {
              "-base": "gml:AbstractFeatureType",
              "sequence": {
                "element": [
                  {
                    "-name": "baumid",
                    "-minOccurs": "0",
                    "-type": "integer"
                  },
                  {
                    "-name": "gattung",
                    "-minOccurs": "0",
                    "-type": "string"
                  },
                  {
                    "-name": "art_latein",
                    "-minOccurs": "0",
                    "-type": "string"
                  },
                  {
                    "-name": "art_deutsch",
                    "-minOccurs": "0",
                    "-type": "string"
                  },
                  {
                    "-name": "sorte",
                    "-minOccurs": "0",
                    "-type": "string"
                  },
                  {
                    "-name": "pflanzjahr",
                    "-minOccurs": "0",
                    "-type": "integer"
                  },
                  {
                    "-name": "kronendurchmesser",
                    "-minOccurs": "0",
                    "-type": "integer"
                  },
                  {
                    "-name": "kronendmzahl",
                    "-minOccurs": "0",
                    "-type": "string"
                  },
                  {
                    "-name": "stammumfang",
                    "-minOccurs": "0",
                    "-type": "integer"
                  },
                  {
                    "-name": "stammumfangzahl",
                    "-minOccurs": "0",
                    "-type": "string"
                  },
                  {
                    "-name": "strasse",
                    "-minOccurs": "0",
                    "-type": "string"
                  },
                  {
                    "-name": "hausnummer",
                    "-minOccurs": "0",
                    "-type": "string"
                  },
                  {
                    "-name": "stand_bearbeitung",
                    "-minOccurs": "0",
                    "-type": "date"
                  },
                  {
                    "-name": "bezirk",
                    "-minOccurs": "0",
                    "-type": "string"
                  },
                  {
                    "-name": "geom",
                    "-minOccurs": "0",
                    "-type": "gml:PointPropertyType"
                  }
                ]
              }
            }
          }
        }
       }
      ]
    ]
  }
}
```
## Other WFS server

Using of [google search](https://www.google.de/search?num=40&client=firefox-b-ab&dcr=0&ei=4I1jWsulNZHXwALmzaywBA&q=inurl%3A%22REQUEST%3DGetFeature%22&oq=inurl%3A%22REQUEST%3DGetFeature%22&gs_l=psy-ab.3...2965.2965.0.3350.1.1.0.0.0.0.0.0..0.0....0...1c..64.psy-ab..1.0.0....0.dB9xZtrbEJ8) you can find a lot of servers:

- [GEOLOGICAL SURVEY
OF DENMARK AND GREENLAND ](http://data.geus.dk/geusmap/ows/4258.jsp?service=wfs&version=1.1.0&request=GetCapabilities)
- [Nationalparkverwaltung Niedersächsisches Wattenmeer](http://mdi.niedersachsen.de/geoserver/MSRL-D5-Eutrophierung/wfs?service=wfs&version=1.1.0&request=GetCapabilities)
- [WFPGeoNode](https://geonode.wfp.org/geoserver/wfs?service=wfs&version=1.1.0&request=GetCapabilities)
- [GeoNetwork opensource page](http://w3.fylde.gov.uk/geoserver/inspire/ows?service=wfs&version=1.1.0&request=GetCapabilities)
- [Louisiana Govenor's Office of Homeland Security and Emergency Preparedness](http://gocop.gohsep.la.gov/geoserver/wfs?service=wfs&version=1.1.0&request=GetCapabilities)
- [Hamburger MeldeMichel](https://geodienste.hamburg.de/HH_WFS_MML_extern?service=WFS&version=1.1.0&request=GetCapabilities)
- [Hamburger KehrWiederBecher](https://geodienste.hamburg.de/HH_WFS_KehrwiederBecher?service=WFS&version=1.1.0&request=GetCapabilities)
- [Hamburger Kitas](https://geodienste.hamburg.de/HH_WFS_KitaEinrichtung?service=WFS&version=1.1.0&request=GetCapabilities)
- [Deutscher Wetterdienst](https://maps.dwd.de/geoserver/dwd/ows?service=WFS&version=1.1.0&request=GetCapabilities)
- [Deutsche Putenzüchter (Bundesministerium für Ernährung und Landwirtschaft)](https://gdi-services.bmel.de/cgi-bin/gefluegel_2013?service=wfs&version=1.1.0&request=GetCapabilities)
- [Wasserpegelstände (Wasserstraßen- und Schifffahrtsverwaltung des Bundes)](http://www.pegelonline.wsv.de/webservices/gis/aktuell/wfsservice=wfs&version=1.1.0&request=GetCapabilities)
- [Haltestellen Informationssystem (ZVBN)](http://daten.zvbn.de/geoserver/zvbn/ows?service=WFS&version=1.1.0&request=GetCapabilities)
- [Hamburger Krankenhäuser](https://geodienste-hamburg.de/HH_WFS_Krankenhaeuser?service=WFS&version=1.1.0&request=GetCapabilities)
