# Ti.WFS
Client for  Web Feature Service (Open Geospatial) for Axway Titanium

With this module you can use WFS services.

### Usage

```
var Wfs = require("ti.wfs");
Wfs.setEndpoint("https://geodienste.hamburg.de/HH_WFS_Strassenbaumkataster");
Wfs.setVersion("2.0.0");
Wfs.requestFeature({
   region : region,
   typeNames : "app:Strassenbaumkataster"
},onload: function(e){
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
      },
      {
        "app:strassenbaumkataster": {
          "-xmlns:app": "http://www.deegree.org/app",
          "-gml:id": "APP_STRASSENBAUMKATASTER_6388",
          "app:baumid": "100076257",
          "app:gattung": "Acer / Ahorn",
          "app:gattung_latein": "Acer",
          "app:gattung_deutsch": "Ahorn",
          "app:art": "Acer platanoides / Spitz-Ahorn",
          "app:art_latein": "Acer platanoides",
          "app:art_deutsch": "Spitz-Ahorn",
          "app:sorte_latein": "Acer platanoides",
          "app:sorte_deutsch": "Spitz-Ahorn",
          "app:pflanzjahr": "1982",
          "app:kronendurchmesser": "9",
          "app:kronendmzahl": "9 m",
          "app:stammumfang": "113",
          "app:stammumfangzahl": "113 cm",
          "app:strasse": "Harburger Chaussee",
          "app:hausnummer": "123",
          "app:stand_bearbeitung": "2017-01-01",
          "app:bezirk": "Hamburg-Mitte",
          "app:geom": {
            "gml:Point": {
              "-gml:id": "APP_STRASSENBAUMKATASTER_6388_APP_GEOM",
              "-srsName": "EPSG:25832",
              "gml:pos": "566535.123 5930620.113"
            }
          }
        }
      }]
    }  
}      
```
